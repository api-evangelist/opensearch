# OpenSearch

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
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

**Areas:** OpenSearch · Search · Analytics · Observability · Open Source · Security

## OpenSearch on APIs.io

Everything profiled for OpenSearch is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/opensearch/](https://apis.io/providers/opensearch/)** — or go straight to one of the APIs or properties below.

### APIs (15)

- [OpenSearch Search and Indexing REST API](https://apis.io/apis/opensearch/opensearch-search-api/) — The core OpenSearch REST API for indexing documents, performing search queries (full text, vector, hybrid), aggregations, and managing indices, mappings,…
- [OpenSearch Account API](https://apis.io/apis/opensearch/opensearch-account-api/) — Self-service account endpoints for the calling user.
- [OpenSearch Action Groups API](https://apis.io/apis/opensearch/opensearch-action-groups-api/) — Reusable groups of cluster and index permissions.
- [OpenSearch Allowlist API](https://apis.io/apis/opensearch/opensearch-allowlist-api/) — Allowlist of HTTP APIs available to non-admin users.
- [OpenSearch Audit API](https://apis.io/apis/opensearch/opensearch-audit-api/) — Audit log configuration.
- [OpenSearch Cache API](https://apis.io/apis/opensearch/opensearch-cache-api/) — Manage the security cache.
- [OpenSearch Certificates API](https://apis.io/apis/opensearch/opensearch-certificates-api/) — Inspect SSL certificates loaded by the cluster.
- [OpenSearch Health API](https://apis.io/apis/opensearch/opensearch-health-api/) — Security plugin health check.
- [OpenSearch Internal Users API](https://apis.io/apis/opensearch/opensearch-internal-users-api/) — CRUD for internal user database entries.
- [OpenSearch Nodes DN API](https://apis.io/apis/opensearch/opensearch-nodes-dn-api/) — Allowlisted distinguished names for cross-cluster nodes.
- [OpenSearch Role Mappings API](https://apis.io/apis/opensearch/opensearch-role-mappings-api/) — Map users, backend roles, and hosts to security roles.
- [OpenSearch Roles API](https://apis.io/apis/opensearch/opensearch-roles-api/) — CRUD for security roles and their permissions.
- [OpenSearch Security Config API](https://apis.io/apis/opensearch/opensearch-security-config-api/) — Inspect and update the running security configuration.
- [OpenSearch SSL Info API](https://apis.io/apis/opensearch/opensearch-ssl-info-api/) — Inspect SSL handshake information for the calling client.
- [OpenSearch Tenants API](https://apis.io/apis/opensearch/opensearch-tenants-api/) — Multi-tenancy support for OpenSearch Dashboards.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/opensearch/](https://apis.io/graphqls/opensearch/opensearch-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [MCP Server](https://apis.io/servers/opensearch/mcp-server/)

#### Agent skills (10)

Agent skills built on the API.

- [aoss-nextgen-provisioning](https://apis.io/agent-skills/opensearch/aoss-nextgen-provisioning/)
- [aws-setup](https://apis.io/agent-skills/opensearch/aws-setup/)
- [cloud](https://apis.io/agent-skills/opensearch/cloud/)
- [log-analytics](https://apis.io/agent-skills/opensearch/log-analytics/)
- [observability](https://apis.io/agent-skills/opensearch/observability/)
- [opensearch-launchpad](https://apis.io/agent-skills/opensearch/opensearch-launchpad/)
- [opensearch-skills](https://apis.io/agent-skills/opensearch/opensearch-skills/)
- [search](https://apis.io/agent-skills/opensearch/search/)
- [solr-opensearch-migration-advisor](https://apis.io/agent-skills/opensearch/solr-opensearch-migration-advisor/)
- [trace-analytics](https://apis.io/agent-skills/opensearch/trace-analytics/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Opensearch Agentic Access](https://apis.io/agentic-access/opensearch/opensearch-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [OpenSearch Security Role](https://apis.io/schemas/opensearch/opensearch-role/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Opensearch Context](https://apis.io/jsonld/opensearch/opensearch-context/)

#### Collections (15)

Postman and Open Collection request collections.

- [OpenSearch Security Plugin REST Account API](https://apis.io/collections/opensearch/open-opensearch-account-api/)
- [OpenSearch Security Plugin REST Account Action Groups API](https://apis.io/collections/opensearch/open-opensearch-action-groups-api/)
- [OpenSearch Security Plugin REST Account Allowlist API](https://apis.io/collections/opensearch/open-opensearch-allowlist-api/)
- [OpenSearch Security Plugin REST Account Audit API](https://apis.io/collections/opensearch/open-opensearch-audit-api/)
- [OpenSearch Security Plugin REST Account Cache API](https://apis.io/collections/opensearch/open-opensearch-cache-api/)
- [OpenSearch Security Plugin REST Account Certificates API](https://apis.io/collections/opensearch/open-opensearch-certificates-api/)
- [OpenSearch Security Plugin REST Account Health API](https://apis.io/collections/opensearch/open-opensearch-health-api/)
- [OpenSearch Security Plugin REST Account Internal Users API](https://apis.io/collections/opensearch/open-opensearch-internal-users-api/)
- [OpenSearch Security Plugin REST Account Nodes DN API](https://apis.io/collections/opensearch/open-opensearch-nodes-dn-api/)
- [OpenSearch Security Plugin REST Account Role Mappings API](https://apis.io/collections/opensearch/open-opensearch-role-mappings-api/)
- [OpenSearch Security Plugin REST Account Roles API](https://apis.io/collections/opensearch/open-opensearch-roles-api/)
- [OpenSearch Security Plugin REST API](https://apis.io/collections/opensearch/open-opensearch-security/)
- [OpenSearch Security Plugin REST Account Security Config API](https://apis.io/collections/opensearch/open-opensearch-security-config-api/)
- [OpenSearch Security Plugin REST Account SSL Info API](https://apis.io/collections/opensearch/open-opensearch-ssl-info-api/)
- [OpenSearch Security Plugin REST Account Tenants API](https://apis.io/collections/opensearch/open-opensearch-tenants-api/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [OpenSearch — jsonschema rules](https://apis.io/rules/opensearch/opensearch-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Opensearch Authentication](https://apis.io/security/opensearch/opensearch-authentication/)
- [Opensearch Domain Security](https://apis.io/security/opensearch/opensearch-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Opensearch Plans Pricing](https://apis.io/plans/opensearch/opensearch-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Opensearch Rate Limits](https://apis.io/rate-limits/opensearch/opensearch-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Opensearch Finops](https://apis.io/finops/opensearch/opensearch-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://opensearch.org/)
- [Documentation](https://docs.opensearch.org/latest/api-reference/)
- [Getting started](https://docs.opensearch.org/latest/getting-started/)
- [Blog](https://opensearch.org/blog/)
- [Security](https://opensearch.org/security)
- [GitHub](https://github.com/opensearch-project)

## API Evangelist rating

**Kin Score 37.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 65.0 |
| Contract quality | 49.3 |
| Contract governance | 9.8 |
| Operational transparency | 23.7 |
| Developer ergonomics | 54.0 |
| Access clarity | 7.9 |

**Agent readiness 24.2** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | unknown |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/opensearch/](https://apis.io/providers/opensearch/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for OpenSearch: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/opensearch/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
