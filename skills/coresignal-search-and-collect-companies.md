---
name: Search and collect Coresignal company records
description: >-
  Find companies matching a set of criteria and retrieve their full records, using Coresignal's
  two-step search-then-collect flow without wasting credits.
api: openapi/coresignal-search-api-openapi.yml, openapi/coresignal-collect-api-openapi.yml
operations: [searchCompaniesByFilter, searchCompaniesByEsDsl, collectCompany]
generated: '2026-08-13'
method: generated
source: >-
  openapi/_original/coresignal-multi-source-company-api-openapi.yml,
  conventions/coresignal-conventions.yml, errors/coresignal-error-codes.yml,
  plans/coresignal-plans-pricing.yml
---

# Search and collect Coresignal company records

## The one thing to understand first

Coresignal search returns **IDs, not records**. Search is free; collect is what costs credits. Never
collect a record you have not first confirmed you want — every `collectCompany` on a Multi-source
record spends 20 credits and there is no test mode and no refund.

## Authenticate

Every request carries the header `apikey: <your 32-character key>`. There is no bearer token, no
OAuth, and no scope on the REST API. Get or rotate the key at
<https://dashboard.coresignal.com/> under **API keys**.

Base URL: `https://api.coresignal.com/cdapi/v2/multi_source_company`

## Step 1 — search (free)

Pick one of two operations:

- `searchCompaniesByFilter` — `POST /search/filter` with a structured `CompanyFilter` body. Use this
  when your criteria map onto the published filter fields: `name`, `industry`, `size`, `country`,
  `region`, `founded_from`, `founded_to`, `employees_count_from`, `employees_count_to`,
  `technologies`.
- `searchCompaniesByEsDsl` — `POST /search/es_dsl` with a raw Elasticsearch Query DSL body. Use this
  when you need boolean logic, ranges, or field combinations the filter object cannot express.

Both return an array of integer company IDs. Neither deducts credits.

## Step 2 — page through the IDs

Results come 1,000 IDs at a time. Read the response headers:

- `x-total-results` — how many IDs matched in total.
- `x-total-pages` — how many pages that is.
- `x-next-page-after` — the opaque cursor for the next page.

Fetch the next page by appending the cursor verbatim: `?after={x-next-page-after}`. Set
`?items_per_page={int}` (max 1,000) if you want smaller pages.

**Check `x-total-results` before collecting anything.** A query matching 56,940 companies costs
1,138,800 credits to collect in full. Narrow the query first.

## Step 3 — collect (charged)

`collectCompany` — `GET /collect/{id}` returns the full `Company` record: identity
(`name`, `website`, `domain`, `linkedin_url`), firmographics (`industry`, `founded`,
`employees_count`, `size`), location (`headquarters`, `country`, `region`, `locality`), and
commercial signal (`technologies`, `funding_total_amount`, `last_funding_round`). Every record
carries `last_updated` — use it, freshness is the product.

Read `x-credits-remaining` on each response to track spend.

For more than a handful of IDs, use `bulkCollectCompanies` instead — see
`skills/coresignal-bulk-collect-at-scale.md`.

## Error handling

| Status | What it actually means | Do |
|---|---|---|
| 401 | The `apikey` header is missing or invalid | Fix the key; do not retry |
| 402 | Out of credits | Stop. Retrying will not succeed |
| 404 | Either a bad URL **or** an id not in the database | Check the path first, then treat as a data miss |
| 422 | Bad request structure or types | Validate against the filter / ES DSL schema |
| 429 | Rate limit exceeded (5–100 req/s depending on plan) | Back off and retry. No `Retry-After` is sent |
| 503 | Elasticsearch overloaded or query too complex | Simplify the query, then retry with backoff |

Errors are a flat `{"detail": "..."}` object — there is no error code registry and no
`application/problem+json`. Branch on the HTTP status, never on the message text.

## Do not

- Do not assume an idempotency key exists. There is none. A retried POST is a new request.
- Do not expect `X-RateLimit-*` headers. They are not sent — you only learn your budget by hitting 429.
- Do not reuse a company `id` across dataset tiers. Base, Clean and Multi-source are separate ID
  spaces reached through separate base paths.
