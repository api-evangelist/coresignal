# Coresignal (coresignal)

Coresignal is a data-as-a-service company providing access to public web data on companies, employees, and jobs through a suite of REST APIs. The platform aggregates and refines more than 4.5 billion data records covering 75M+ companies (with 500+ data fields), 865M+ employee profiles (300+ fields), and 461M+ job postings (85+ fields). Coresignal offers Multi-source, Clean, and Base data tiers across Company, Employee, and Jobs APIs, plus specialized real-time, employee posts, agentic search, and company enrichment endpoints.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/coresignal/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party
- **x-type:** company

## Tags

- Agentic Search, B2B Data, Companies, Company Data, Data as a Service, Elasticsearch, Employee Data, Employees, Enrichment, Firmographics, Job Postings, Jobs, Lead Generation, People Data, Sales Intelligence, Talent Intelligence, Web Data

## Timestamps

- **Created:** 2025-02-12
- **Modified:** 2026-04-28

## APIs

### Coresignal Multi-source Company API

Enriched company records combining data from multiple public web sources with 500+ data fields. Search via filters or Elasticsearch DSL; Collect and Bulk Collect endpoints retrieve full records by ID.

- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_company`
- [Documentation](https://docs.coresignal.com/multi-source-company-api/)
- [OpenAPI](openapi/coresignal-multi-source-company-api-openapi.yml)
- [Rules](rules/coresignal-multi-source-company-api-rules.yml)
- [Capabilities](capabilities/coresignal-company-data-collection-capabilities.yml)

### Coresignal Multi-source Employee API

Enriched employee profiles aggregated from multiple public sources with 300+ fields covering experience, education, skills, certifications, and connections.

- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_employee`
- [Documentation](https://docs.coresignal.com/multi-source-employee-api/)
- [OpenAPI](openapi/coresignal-multi-source-employee-api-openapi.yml)
- [Rules](rules/coresignal-multi-source-employee-api-rules.yml)
- [Capabilities](capabilities/coresignal-employee-data-collection-capabilities.yml)

### Coresignal Multi-source Jobs API

Enriched job posting records aggregated from multiple public sources with 85+ data fields covering title, location, company, salary, posted date, and full descriptions.

- **Base URL:** `https://api.coresignal.com/cdapi/v2/multi_source_jobs`
- [Documentation](https://docs.coresignal.com/multi-source-jobs-api/)
- [OpenAPI](openapi/coresignal-multi-source-jobs-api-openapi.yml)
- [Rules](rules/coresignal-multi-source-jobs-api-rules.yml)
- [Capabilities](capabilities/coresignal-jobs-data-collection-capabilities.yml)

### Coresignal Agentic Search API

Natural language search across company, employee, and jobs datasets for AI agents and automated workflows.

- [Documentation](https://docs.coresignal.com/agentic-search-api/)

### Coresignal Company Enrichment API

Real-time enrichment of CRM records or web form submissions by domain or company name.

- [Documentation](https://docs.coresignal.com/company-enrichment-api/)

## Common Properties

- [Website](https://coresignal.com)
- [Developer Portal](https://docs.coresignal.com/)
- [Authorization](https://docs.coresignal.com/api-introduction/authorization)
- [Rate Limits](https://docs.coresignal.com/api-introduction/rate-limits)
- [Vocabulary](vocabulary/coresignal-vocabulary.yml)
- [JSON-LD Context](json-ld/coresignal-context.jsonld)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
