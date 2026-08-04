# Coresignal (coresignal)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Coresignal is a data-as-a-service company providing access to public web data on companies, employees, and jobs through a suite of REST APIs. The platform aggregates and refines more than 4.5 billion data records covering 75M+ companies (with 500+ data fields), 865M+ employee profiles (300+ fields), and 461M+ job postings (85+ fields). Coresignal offers Multi-source, Clean, and Base data tiers across Company, Employee, and Jobs APIs, plus specialized real-time, employee posts, agentic search, and company enrichment endpoints. Authentication uses a single apikey HTTP header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/coresignal/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/coresignal/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Agentic Search
- B2B Data
- Companies
- Company Data
- Data as a Service
- Elasticsearch
- Employee Data
- Employees
- Enrichment
- Firmographics
- Job Postings
- Jobs
- Lead Generation
- People Data
- Sales Intelligence
- Talent Intelligence
- Web Data

## Timestamps

- **Created:** 2025-02-12
- **Modified:** 2026-05-19

## APIs

### Coresignal Multi-source Company API

The Multi-source Company API returns enriched company records combining data from multiple public web sources, deduplicated and standardized with 500+ data fields covering firmographics, technographics, headcount, revenue, and locations. Search uses Elasticsearch DSL. Results are paginated and credits-priced per response.

- **Human URL:** [https://docs.coresignal.com/multi-source-company-api/](https://docs.coresignal.com/multi-source-company-api/)
- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_company`

#### Tags

- Companies
- Firmographics
- Multi-source

#### Properties

- [Documentation](https://docs.coresignal.com/multi-source-company-api/)
- [Data Dictionary](https://docs.coresignal.com/multi-source-company-api/data-dictionary)
- [Sample](https://docs.coresignal.com/multi-source-company-api/sample)
- [Search Filters](https://docs.coresignal.com/multi-source-company-api/search-filters)
- [Elasticsearch D S L](https://docs.coresignal.com/multi-source-company-api/search-with-es-dsl)
- [Collect](https://docs.coresignal.com/multi-source-company-api/collect)
- [Bulk Collect](https://docs.coresignal.com/multi-source-company-api/bulk-collect)
- [Webhooks](https://docs.coresignal.com/multi-source-company-api/subscriptions)
- [OpenAPI](openapi/coresignal-multi-source-company-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/coresignal-multi-source-company-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-company-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Rules](rules/coresignal-multi-source-company-api-rules.yml)
- [Capabilities](capabilities/coresignal-company-data-collection-capabilities.yml)

### Coresignal Multi-source Employee API

The Multi-source Employee API returns enriched employee profiles aggregated from multiple public sources with 300+ data fields covering experience, education, skills, certifications, and connections. Search uses Elasticsearch DSL with rich filter support, pagination, and collect/bulk_collect endpoints for retrieving full records by ID.

- **Human URL:** [https://docs.coresignal.com/multi-source-employee-api/](https://docs.coresignal.com/multi-source-employee-api/)
- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_employee`

#### Tags

- Employees
- Multi-source
- People Data

#### Properties

- [Documentation](https://docs.coresignal.com/multi-source-employee-api/)
- [Data Dictionary](https://docs.coresignal.com/multi-source-employee-api/data-dictionary)
- [Sample](https://docs.coresignal.com/multi-source-employee-api/sample)
- [Search Filters](https://docs.coresignal.com/multi-source-employee-api/search-filters)
- [Elasticsearch D S L](https://docs.coresignal.com/multi-source-employee-api/search-with-es-dsl)
- [Collect](https://docs.coresignal.com/multi-source-employee-api/collect)
- [Bulk Collect](https://docs.coresignal.com/multi-source-employee-api/bulk-collect)
- [Webhooks](https://docs.coresignal.com/multi-source-employee-api/subscriptions)
- [OpenAPI](openapi/coresignal-multi-source-employee-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/coresignal-multi-source-employee-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-employee-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Rules](rules/coresignal-multi-source-employee-api-rules.yml)
- [Capabilities](capabilities/coresignal-employee-data-collection-capabilities.yml)

### Coresignal Multi-source Jobs API

The Multi-source Jobs API returns enriched job posting records aggregated from multiple public sources with 85+ data fields covering title, location, company, salary, posted date, source URLs, and full job descriptions. Search uses Elasticsearch DSL with collect endpoints for retrieving full records by ID.

- **Human URL:** [https://docs.coresignal.com/multi-source-jobs-api/](https://docs.coresignal.com/multi-source-jobs-api/)
- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_jobs`

#### Tags

- Jobs
- Multi-source
- Recruiting

#### Properties

- [Documentation](https://docs.coresignal.com/multi-source-jobs-api/)
- [Data Dictionary](https://docs.coresignal.com/multi-source-jobs-api/data-dictionary)
- [Sample](https://docs.coresignal.com/multi-source-jobs-api/sample)
- [Search Filters](https://docs.coresignal.com/multi-source-jobs-api/search-filters)
- [Elasticsearch D S L](https://docs.coresignal.com/multi-source-jobs-api/search-with-es-dsl)
- [Collect](https://docs.coresignal.com/multi-source-jobs-api/collect)
- [OpenAPI](openapi/coresignal-multi-source-jobs-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/coresignal-multi-source-jobs-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-jobs-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Rules](rules/coresignal-multi-source-jobs-api-rules.yml)
- [Capabilities](capabilities/coresignal-jobs-data-collection-capabilities.yml)

### Coresignal Agentic Search API

The Agentic Search API enables natural language search across Coresignal's company, employee, and jobs datasets, returning relevant records based on conversational queries. Designed for AI agents and automated workflows that need quick B2B data lookups without crafting Elasticsearch queries.

- **Human URL:** [https://docs.coresignal.com/agentic-search-api/](https://docs.coresignal.com/agentic-search-api/)
- **Base URL:** `https://api.coresignal.com/cdapi/v2/agentic_search`

#### Tags

- Agentic Search
- AI Agents
- Natural Language

#### Properties

- [Documentation](https://docs.coresignal.com/agentic-search-api/)
- [Postman Collection](collections/coresignal-multi-source-company-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-company-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/coresignal-multi-source-employee-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-employee-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/coresignal-multi-source-jobs-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-jobs-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Coresignal Company Enrichment API

The Company Enrichment API takes a company domain or name and returns a fully-enriched company record. Designed for sales and marketing systems that need to enrich CRM records or web form submissions in real time.

- **Human URL:** [https://docs.coresignal.com/company-enrichment-api/](https://docs.coresignal.com/company-enrichment-api/)
- **Base URL:** `https://api.coresignal.com/cdapi/v2/company_enrichment`

#### Tags

- Companies
- Enrichment
- CRM

#### Properties

- [Documentation](https://docs.coresignal.com/company-enrichment-api/)
- [Postman Collection](collections/coresignal-multi-source-company-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-company-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/coresignal-multi-source-employee-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-employee-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/coresignal-multi-source-jobs-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coresignal-multi-source-jobs-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [GitHub Organization](https://github.com/Coresignal-com)
- [Website](https://coresignal.com)
- [Developer Portal](https://docs.coresignal.com/)
- [Documentation](https://docs.coresignal.com/)
- [A P Is Overview](https://docs.coresignal.com/api-introduction/apis-overview)
- [Authorization](https://docs.coresignal.com/api-introduction/authorization)
- [Getting Started](https://docs.coresignal.com/api-introduction/getting-started)
- [Rate Limits](https://docs.coresignal.com/api-introduction/rate-limits)
- [Response Codes](https://docs.coresignal.com/api-introduction/response-codes)
- [Credits](https://docs.coresignal.com/api-introduction/credits)
- [Webhooks](https://docs.coresignal.com/api-introduction/webhooks)
- [Dashboard](https://dashboard.coresignal.com/sign-in)
- [Sign Up](https://dashboard.coresignal.com/sign-up)
- [Pricing](https://coresignal.com/pricing/)
- [Solutions](https://coresignal.com/solutions/)
- [Use Cases](https://coresignal.com/use-cases/)
- [Blog](https://coresignal.com/blog/)
- [Vocabulary](vocabulary/coresignal-vocabulary.yml)
- [JSON-LD](json-ld/coresignal-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Privacy Policy](https://coresignal.com/privacy-policy/)
- [Terms of Service](https://coresignal.com/terms-and-conditions/)
- [Status Page](https://status.coresignal.com/)
- [LinkedIn](https://www.linkedin.com/company/coresignal)
- [Twitter](https://twitter.com/coresignal)
- [L L Ms Txt](https://docs.coresignal.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
