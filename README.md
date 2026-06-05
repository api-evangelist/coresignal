# Coresignal (coresignal)

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
