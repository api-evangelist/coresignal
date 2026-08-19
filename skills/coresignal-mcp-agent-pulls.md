---
name: Pull Coresignal data from an agent over MCP
description: >-
  Connect to the Coresignal MCP server and run natural-language searches, field discovery and record
  fetches without burning credits on exploratory queries.
api: mcp/coresignal-mcp.yml
operations: [entity_search, entity_fields, entity_fetch, email_enrich, artifact_read]
generated: '2026-08-13'
method: generated
source: >-
  https://docs.coresignal.com/integrations/coresignal-mcp,
  https://github.com/Coresignal-com/coresignal-mcp, mcp/coresignal-mcp.yml,
  mcp/coresignal-tool-crosswalk.yml
---

# Pull Coresignal data from an agent over MCP

## Connect

Remote server, streamable HTTP, no install:

```
https://mcp.coresignal.com/mcp/v2
```

```bash
claude mcp add --transport http coresignal https://mcp.coresignal.com/mcp/v2
```

Authentication is **OAuth 2.1** against the Coresignal dashboard — the first connection opens a
browser sign-in. No API key ever goes in a config file; the server resolves the signed-in team's key
server-side. Discovery: `https://mcp.coresignal.com/.well-known/oauth-protected-resource/mcp/v2` →
authorization server `https://dashboard.coresignal.com/api/auth`, PKCE S256, dynamic client
registration supported.

The older endpoint `https://mcp.coresignal.com/mcp` still works with an `apikey` header and exposes
three raw Elasticsearch-DSL tools, but Coresignal states it will eventually be deprecated. Use v2.

## The credit discipline — read this before your first call

The token carries **no scopes** (`scopes_supported: []`). Once signed in, an agent can spend the
whole team's credit balance. There is no read-only mode. Sequence your calls so the free ones do the
exploring:

| Tool | Cost | Use it to |
|---|---|---|
| `entity_fields` | **free** | Find the right field names before you scope anything |
| `entity_search` | 20 credits flat | Get `total_count` + up to 20 preview rows + a `cache_id` |
| `entity_fetch` | 20/record (employee, company), 1/record (job) | Pull the records you actually want |
| `email_enrich` | 10 per email **found** | Verified business emails; misses are free |
| `artifact_read` | free | Page rows back out of a delivered file |

## The efficient sequence

1. **`entity_fields`** — search the ~300 field names by meaning (`"salary"`, `"current job title"`).
   Free, unlimited, and it stops you loading the whole field vocabulary into context.
2. **`entity_search`** — describe the population in plain language. Flat 20 credits regardless of
   result size. It returns `total_count` (exact), up to 20 preview rows showing *which fields
   matched*, and a `cache_id`.
3. **Check `total_count` before fetching.** 8,000 employee records is 160,000 credits.
4. **`entity_fetch`** with the `cache_id`. Resolving a `cache_id` is free and it holds for **1 hour**
   — reusing it avoids re-running and re-paying for the search. Up to 1,000 records per call via the
   handle, or up to 20 hand-picked ids.
5. Large results come back as a **downloadable file link**, not inline. In Claude Desktop you must
   add `mcp.coresignal.com` to the domain allowlist for downloads to work — or skip downloads
   entirely and page the rows back in-chat with the free `artifact_read`.

Use `limit=0` on `entity_search` when you only want the count.

## Legal and coverage limits

`email_enrich` **automatically excludes employees in the EEA and the UK** for GDPR compliance.
Blocked lookups are not charged. Do not build a workflow that assumes European coverage on emails.

## What MCP cannot do that REST can

- **Structured filter search** — the v2 tools take natural language only. If you need an explicit
  filter object or hand-written Elasticsearch DSL, use `searchCompaniesByFilter` /
  `searchCompaniesByEsDsl` over REST.
- **Bulk Collect** — `entity_fetch` caps at 1,000 records per call. The 10,000-ID asynchronous bulk
  job has no tool.
- **Webhook subscriptions** — no tool; use the REST `/v2/subscriptions` endpoints.

The full mapping between tools and REST operations is in `mcp/coresignal-tool-crosswalk.yml`.

## Confirmations

The server pauses and asks before a large or expensive retrieval, and every response reports
`credits_consumed`. Do not suppress or auto-approve those prompts in an unattended agent — they are
the only spend control on this surface.
