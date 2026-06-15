# OpenSearch (opensearch)

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
