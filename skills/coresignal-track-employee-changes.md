---
name: Track employee profile changes with Coresignal webhooks
description: >-
  Subscribe to change notifications on a population of employee profiles, then resolve what actually
  changed — the notification carries no data.
api: openapi/_original/coresignal-multi-source-employee-api-openapi.yml
operations: [searchEmployeesByFilter, searchEmployeesByEsDsl, collectEmployee, bulkCollectEmployees]
generated: '2026-08-13'
method: generated
source: >-
  https://docs.coresignal.com/api-introduction/webhooks,
  asyncapi/coresignal-webhooks.yml, openapi/_original/coresignal-multi-source-employee-api-openapi.yml
---

# Track employee profile changes with Coresignal webhooks

## What a Coresignal webhook is — and is not

It is a **change notification**, not a data delivery. The payload tells you *which profile changed*
and *which fields*, and nothing else. Getting the new values is a separate, credit-charged
`collectEmployee` or `bulkCollectEmployees` call. Notifications themselves cost no credits, so the
webhook surface is a way to spend credits only on records that actually moved.

Webhooks exist for **employee profiles only**. There is no company or jobs webhook.

## Step 1 — define the tracked population

Three selectors, all documented:

- an explicit list of employee IDs,
- a search-filter query (the same `EmployeeFilter` shape `searchEmployeesByFilter` takes),
- an Elasticsearch DSL query (the same body `searchEmployeesByEsDsl` takes).

**Date filters are not allowed in a subscription query** — from either the search-filter set or the
ES DSL schema. Including one returns 422.

Optionally add `tracked_fields` to narrow further: `{"tracked_fields": ["skills"]}` fires only on
`skills` changes across your tracked population, ignoring everything else.

## Step 2 — subscribe and manage

| Method | Path | Purpose |
|---|---|---|
| GET | `/cdapi/v2/subscriptions?expired={bool}&page={int}` | List subscriptions (~1,000 per page) with `status`, `created_at`, `expiring_at` |
| GET | `/cdapi/v2/subscriptions/{subscription_id}` | Detail of one active subscription |
| POST | `/cdapi/v2/subscriptions/{subscription_id}/renew` | Renew, up to 1 year total from creation |
| DELETE | `/cdapi/v2/subscriptions/{subscription_id}` | Delete |
| POST | `/cdapi/v2/subscriptions/simulate` | Deliver one example webhook immediately, body `{"webhook_url": "..."}` |

Limits: **91-day** subscription lifetime, renewable to a maximum of 1 year from creation; **500**
subscriptions per account; **300,000** IDs per subscription.

Test your receiver with `/subscriptions/simulate` before going live — otherwise you wait a full
delivery cycle to discover a broken endpoint.

## Step 3 — handle the payload

Deliveries are **JSON arrays**, many profiles per POST:

```json
[
  {"member_id": 123, "status": "started_matching_query", "changed_fields": null},
  {"member_id": 124, "status": "stopped_matching_query", "changed_fields": null},
  {"member_id": 125, "status": "changed", "changed_fields": ["skills", "headline", "certifications"]}
]
```

`member_id` is the employee `id`. The three statuses:

- `started_matching_query` — the profile newly matches your filters (e.g. a title changed to
  "Project Manager"). This is your *new lead* signal.
- `stopped_matching_query` — the profile no longer matches. This is your *churn / stale record*
  signal.
- `changed` — tracked fields moved; `changed_fields` names them.

Experience webhooks are a separate channel with a slimmer payload (`member_id` + `status: changed`)
and fire when someone starts or closes a position — the career-movement signal.

## Step 4 — resolve the change

Use `changed_fields` to decide whether the change is worth paying for. If it is, `collectEmployee`
for one profile or `bulkCollectEmployees` for the batch. If `changed_fields` contains nothing you
care about, drop the notification and spend nothing.

## Cadence

| Source | Frequency |
|---|---|
| Base Employee API | Daily |
| Clean Employee API | Weekly |
| Multi-source Employee API | Weekly |

## Verify the sender yourself

Coresignal documents **no payload signature, no retry policy and no delivery ordering guarantee**.
Your endpoint cannot cryptographically confirm a delivery came from Coresignal. Mitigate with a
long unguessable callback path, an IP or mTLS allowlist at your edge if you can obtain one, and
idempotent handling on your side keyed on `member_id` — assume a delivery may arrive twice or out of
order.
