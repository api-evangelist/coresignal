---
name: Bulk collect Coresignal records at scale
description: >-
  Submit, poll and retrieve large Coresignal datasets with Bulk Collect, without double-spending
  credits on a resubmitted job.
api: openapi/coresignal-collect-api-openapi.yml, openapi/_original/coresignal-multi-source-employee-api-openapi.yml
operations: [searchCompaniesByEsDsl, bulkCollectCompanies, searchEmployeesByEsDsl, bulkCollectEmployees]
generated: '2026-08-13'
method: generated
source: >-
  openapi/_original/*.yml, errors/coresignal-error-codes.yml,
  conventions/coresignal-conventions.yml, arazzo/coresignal-company-esdsl-bulk-collect-workflow.yml
---

# Bulk collect Coresignal records at scale

Use this instead of looping `collectCompany` / `collectEmployee` whenever you need more than a few
dozen records.

## Step 1 — build the ID set with a free search

`searchCompaniesByEsDsl` (`POST /search/es_dsl`) or `searchEmployeesByEsDsl` returns IDs and costs
nothing. Page with `?after={x-next-page-after}` until you have collected `x-total-results` IDs, at
1,000 per page.

**Budget check before you go further.** Multiply the ID count by the per-record credit cost (20 for
Multi-source company/employee, 10 for Base/Clean, 1 for jobs and posts). Bulk Collect will spend it
without a confirmation step.

## Step 2 — submit the bulk job

`bulkCollectCompanies` / `bulkCollectEmployees` — `POST /bulk_collect`.

Hard limits:

- **10,000 IDs maximum** per request. Split larger sets; exceeding it returns 422.
- **No duplicates** in the ID list — duplicates also return 422.
- URLs supplied instead of IDs must be parseable into shorthand names, or 422.

A successful submission returns **201**; **202** means the job is still running.

## Step 3 — handle 409 correctly (this is the important one)

If you submit an identical search or Elasticsearch-DSL bulk request while one is already running, you
get:

```
409 {"detail": "Identical data request is already in progress."}
```

This is Coresignal's server-side duplicate detection, and it is protecting your credit balance. **Do
not treat 409 as a failure and retry with a modified query** — that creates a second, chargeable job.
Poll the job you already have.

Note the asymmetry this creates: Coresignal has duplicate *detection* but no idempotency *key*. You
cannot name a request, and if a POST times out you cannot safely replay it to recover the original
job. Log your submissions client-side so you can reconcile.

## Step 4 — retrieve within the window

The prepared dataset can be downloaded as often as you like for **30 days** from query submission.
After 30 days the GET returns **404**. Persist the data on your side inside that window; there is no
extension and no archive.

## Errors specific to bulk

| Status | Meaning | Do |
|---|---|---|
| 201 | Accepted | Poll |
| 202 | In progress | Keep polling |
| 400 | Malformed or oversized file, invalid data | Fix the input |
| 402 | Insufficient credits | Reduce batch size or buy credits |
| 404 | No matching IDs — or the 30-day window has expired | Check the submission date first |
| 409 | Duplicate in-flight submission | Poll the existing job, do **not** resubmit |
| 422 | >10k IDs, duplicate IDs, or unparseable URLs | Split and de-duplicate |
| 503 | Temporary pipeline disruption | Retry with backoff |

## Ready-made workflows

`arazzo/coresignal-company-esdsl-bulk-collect-workflow.yml` and
`arazzo/coresignal-employee-esdsl-bulk-collect-workflow.yml` implement this end to end.
