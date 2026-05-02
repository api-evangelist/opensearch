# OpenSearch (opensearch)

OpenSearch is the open source, community-driven search, analytics, and observability suite (forked from Elasticsearch and Kibana) maintained under the Linux Foundation's OpenSearch Software Foundation. The platform exposes REST APIs across the search engine, the OpenSearch Dashboards UI, and a set of plugins. The Security plugin REST API lets administrators programmatically create and manage internal users, roles, role mappings, action groups, tenants, security configuration, audit log configuration, and SSL certificates.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Search, Analytics, Observability, Open Source, Security

## Timestamps

- **Created:** 2025-01-08
- **Modified:** 2026-04-28

## APIs

### OpenSearch Security Plugin REST API
The Security plugin REST API lets administrators programmatically create and manage internal users, roles, role mappings, action groups, tenants, security configuration, audit log configuration, allowlists, node DN entries, and SSL certificates. Endpoints are exposed under `/_plugins/_security/api` on the OpenSearch cluster and require authentication.

**Human URL:** [https://docs.opensearch.org/latest/security/access-control/api/](https://docs.opensearch.org/latest/security/access-control/api/)

**Base URL:** https://{cluster-host}:9200

#### Tags

- Security, Access Control, Roles, Authentication

#### Properties

- [Documentation](https://docs.opensearch.org/latest/security/access-control/api/)
- [Documentation](https://docs.opensearch.org/latest/security/access-control/index/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/openapi/opensearch-security-openapi.yml)
- [JSONSchema](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/json-schema/opensearch-role-schema.json)
- [JSONLDContext](https://raw.githubusercontent.com/api-evangelist/opensearch/refs/heads/main/json-ld/opensearch-context.jsonld)

### OpenSearch Search and Indexing REST API
The core OpenSearch REST API for indexing documents, performing search queries (full text, vector, hybrid), aggregations, and managing indices, mappings, templates, aliases, and snapshots.

**Human URL:** [https://docs.opensearch.org/latest/api-reference/](https://docs.opensearch.org/latest/api-reference/)

**Base URL:** https://{cluster-host}:9200

#### Tags

- Search, Indexing, Vector Search, Aggregations

#### Properties

- [Documentation](https://docs.opensearch.org/latest/api-reference/)
- [Documentation](https://docs.opensearch.org/latest/search-plugins/)
- [Reference](https://docs.opensearch.org/latest/api-reference/search/)

## Common Properties

- [Website](https://opensearch.org/)
- [Portal](https://docs.opensearch.org/)
- [Documentation](https://docs.opensearch.org/latest/api-reference/)
- [GettingStarted](https://docs.opensearch.org/latest/getting-started/)
- [Community](https://opensearch.org/community/)
- [Forum](https://forum.opensearch.org/)
- [Blog](https://opensearch.org/blog/)
- [GitHubOrganization](https://github.com/opensearch-project)
- [Security Plugin Repo](https://github.com/opensearch-project/security)
- [OpenSearch Core Repo](https://github.com/opensearch-project/OpenSearch)
- [Download](https://opensearch.org/downloads/)
- [License](https://opensearch.org/license.html)
- [Security](https://opensearch.org/security)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
