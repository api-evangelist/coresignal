---
name: Map a company to its workforce and open roles
description: >-
  Given a company, resolve its employees and its live job postings across Coresignal's three parallel
  datasets — which are joined by value, not by foreign key.
api: >-
  openapi/_original/coresignal-multi-source-company-api-openapi.yml,
  openapi/_original/coresignal-multi-source-employee-api-openapi.yml,
  openapi/_original/coresignal-multi-source-jobs-api-openapi.yml
operations: [searchCompaniesByFilter, collectCompany, searchEmployeesByFilter, collectEmployee, searchJobsByFilter, collectJob]
generated: '2026-08-13'
method: generated
source: >-
  openapi/_original/*.yml, data-model/coresignal-data-model.yml,
  arazzo/coresignal-company-to-employees-workflow.yml, arazzo/coresignal-company-to-jobs-workflow.yml
---

# Map a company to its workforce and open roles

## The trap

There is **no company id on an Employee record and no company id on a Job record.** Coresignal's
three datasets are parallel, not relational. You join them by *string value*:

- Job → Company via `company_name` (or `company_url`, normalized to a domain).
- Employee → Company via the `active_experience_company_name` filter field.

That means a naive join over-matches on common names and under-matches on legal-name variants. Resolve
the canonical company first, then use its exact `name` as the join value.

## Step 1 — resolve the company

`searchCompaniesByFilter` — `POST /cdapi/v2/multi_source_company/search/filter` with
`{"name": "<company>"}`, or filter by `country` + `industry` to disambiguate. Then `collectCompany`
(`GET /collect/{id}`) on the best match and keep three fields: `name`, `website`, `domain`.

Use `website`/`domain` as the tiebreaker whenever two companies share a name. This is the only
reliable disambiguator Coresignal gives you.

## Step 2a — the workforce

`searchEmployeesByFilter` — `POST /cdapi/v2/multi_source_employee/search/filter` with:

```json
{ "active_experience_company_name": "<Company.name>", "active_experience_title": "<optional role>" }
```

`EmployeeFilter` also accepts `full_name`, `title`, `country`, `location`, `industry` and `skills` —
add them to narrow before you spend anything. Then `collectEmployee` (`GET /collect/{id}`) per ID, or
`bulkCollectEmployees` for volume.

An `Employee` record returns `full_name`, `title`, `headline`, `summary`, `skills`,
`certifications`, `connections`, `followers`, and the embedded `experience[]` and `education[]`
arrays. Since 2026-08-01 each entry in those arrays carries its own `id`, so an individual position
is addressable.

## Step 2b — the open roles

`searchJobsByFilter` — `POST /cdapi/v2/multi_source_jobs/search/filter` with
`{"company_name": "<Company.name>", "application_active": true}`. `JobFilter` also accepts `title`,
`country`, `location`, `seniority_level`, `employment_type`, `date_posted_from`, `date_posted_to`.

Then `collectJob` (`GET /collect/{id}`). Jobs are the cheapest records in the catalog — 1 credit each
against 20 for a Multi-source employee — so hiring signal is the affordable way to read a company.

**Schema warning:** as of 2026-08-18 `employment_type` is an **array of strings** (was a single
string) with normalized values, and `salary[].currency` uses ISO 4217 codes instead of symbols.
Handle both shapes if you cached records before that date.

## Step 3 — costs, before you run it

| Record | Credits each |
|---|---|
| Multi-source Company / Employee | 20 |
| Base / Clean Company / Employee | 10 |
| Jobs, Employee Posts, Company Posts | 1 |
| Historical Headcount | 10 |
| Contact Enrichment | 20 |

Search costs nothing, so always read `x-total-results` from the search response and decide the budget
before calling collect. `x-credits-remaining` on each response is your running balance.

## Prefer the ready-made workflows

This repo already ships these chains as executable Arazzo:

- `arazzo/coresignal-company-to-employees-workflow.yml`
- `arazzo/coresignal-company-to-jobs-workflow.yml`
- `arazzo/coresignal-company-search-branch-collect-workflow.yml`

Fork those rather than re-deriving the step order.
