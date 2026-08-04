# OpenSearch (opensearch)

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

OpenSearch is the open source, community-driven search, analytics, and observability suite (forked from Elasticsearch and Kibana) maintained under the Linux Foundation's OpenSearch Software Foundation. The platform exposes REST APIs across the search engine, the OpenSearch Dashboards UI, and a set of plugins. The Security plugin REST API lets administrators programmatically create and manage internal users, roles, role mappings, action groups, tenants, security configuration, audit log configuration, and SSL certificates.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Search
- Analytics
- Observability
- Open Source
- Security

## Timestamps

- **Created:** 2025-01-08
- **Modified:** 2026-05-19

## APIs

### OpenSearch Security Plugin REST API

The Security plugin REST API lets administrators programmatically create and manage internal users, roles, role mappings, action groups, tenants, security configuration, audit log configuration, allowlists, node DN entries, and SSL certificates. Endpoints are exposed under /_plugins/_security/api on the OpenSearch cluster and require authentication.

- **Human URL:** [https://docs.opensearch.org/latest/security/access-control/api/](https://docs.opensearch.org/latest/security/access-control/api/)
- **Base URL:** `https://{cluster-host}:9200`

#### Tags

- Security
- Access Control
- Roles
- Authentication

#### Properties

- [Documentation](https://docs.opensearch.org/latest/security/access-control/api/)
- [Documentation](https://docs.opensearch.org/latest/security/access-control/index/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/openapi/opensearch-security-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [JSON Schema](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/json-schema/opensearch-role-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [J S O N L D Context](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/json-ld/opensearch-context.jsonld)
- [Postman Collection](collections/opensearch-security.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/opensearch-security.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### OpenSearch Search and Indexing REST API

The core OpenSearch REST API for indexing documents, performing search queries (full text, vector, hybrid), aggregations, and managing indices, mappings, templates, aliases, and snapshots.

- **Human URL:** [https://docs.opensearch.org/latest/api-reference/](https://docs.opensearch.org/latest/api-reference/)
- **Base URL:** `https://{cluster-host}:9200`

#### Tags

- Search
- Indexing
- Vector Search
- Aggregations

#### Properties

- [Documentation](https://docs.opensearch.org/latest/api-reference/)
- [Documentation](https://docs.opensearch.org/latest/search-plugins/)
- [Reference](https://docs.opensearch.org/latest/api-reference/search/)
- [Postman Collection](collections/opensearch-security.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/opensearch-security.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/opensearch-project)
- [Website](https://opensearch.org/)
- [Portal](https://docs.opensearch.org/)
- [Documentation](https://docs.opensearch.org/latest/api-reference/)
- [Getting Started](https://docs.opensearch.org/latest/getting-started/)
- [Community](https://opensearch.org/community/)
- [Forum](https://forum.opensearch.org/)
- [Blog](https://opensearch.org/blog/)
- [GitHub Organization](https://github.com/opensearch-project)
- [GitHub Repository](https://github.com/opensearch-project/security)
- [GitHub Repository](https://github.com/opensearch-project/OpenSearch)
- [Download](https://opensearch.org/downloads/)
- [License](https://opensearch.org/license.html)
- [Security](https://opensearch.org/security)
- [M C P Server](https://github.com/opensearch-project/opensearch-mcp-server-py)
- [Agent Skill](https://github.com/opensearch-project/opensearch-agent-skills)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
