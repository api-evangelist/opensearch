# OpenSearch GraphQL Schema

This directory contains a conceptual GraphQL schema for the OpenSearch search, analytics, and observability platform — the open-source, community-driven suite forked from Elasticsearch and Kibana and maintained under the Linux Foundation's OpenSearch Software Foundation.

## Source APIs

| API | Base URL | Docs |
|-----|----------|------|
| OpenSearch Search & Indexing REST API | `https://{cluster-host}:9200` | https://opensearch.org/docs/latest/api-reference/ |
| OpenSearch Security Plugin REST API | `https://{cluster-host}:9200/_plugins/_security/api` | https://docs.opensearch.org/latest/security/access-control/api/ |
| ML Commons Plugin REST API | `https://{cluster-host}:9200/_plugins/_ml` | https://docs.opensearch.org/latest/ml-commons-plugin/api/ |
| k-NN Plugin REST API | `https://{cluster-host}:9200/_plugins/_knn` | https://docs.opensearch.org/latest/search-plugins/knn/api/ |
| Search Pipelines REST API | `https://{cluster-host}:9200/_search/pipeline` | https://docs.opensearch.org/latest/search-plugins/search-pipelines/index/ |

## Schema file

[opensearch-schema.graphql](opensearch-schema.graphql)

## Type inventory

### Index management
| Type | Description |
|------|-------------|
| `Index` | An OpenSearch index with health, status, settings, mappings, aliases, stats, shards, and segments |
| `IndexDetails` | Creation date, UUID, shard/replica counts, and provided name |
| `IndexMapping` | Field mappings, dynamic mapping mode, and dynamic templates |
| `IndexSettings` | Shard count, replicas, refresh interval, codec, analysis config, and sort configuration |
| `IndexAlias` | Named alias pointing to one or more indices with optional filter and routing |
| `IndexStats` | Doc counts, store size, and operation counters for indexing, search, merges, refreshes, and flushes |

### Shard and segment management
| Type | Description |
|------|-------------|
| `Shard` | A single shard allocation including node assignment, state, and doc counts |
| `ShardDetails` | Routing state, relocation info, and unassigned reason |
| `ShardStats` | Per-shard operation counters for indexing, search, merges, translog, and flush |
| `Segment` | A Lucene segment within a shard |
| `SegmentDetails` | Generation, size, committed/search flags, compound state, and Lucene version |

### Document operations
| Type | Description |
|------|-------------|
| `Document` | A stored document with index, id, version, sequence number, and source |
| `DocumentMeta` | Identity metadata: index, id, version, seqNo, primaryTerm, routing |
| `DocumentSource` | Raw JSON fields of a document |

### Search
| Type | Description |
|------|-------------|
| `SearchResult` | Top-level search response with timing, shard stats, hits, and aggregations |
| `SearchHits` | The hits container with total count, max score, and individual hits |
| `SearchHit` | A single matched document with score, highlight, sort values, and inner hits |
| `HitDetails` | Score explanation, matched query names, and nested path metadata |
| `SearchShardStats` | Total, successful, skipped, and failed shard counts for a search |
| `SearchQuery` | The full query DSL body: query, size, from, sort, source filtering, aggregations, etc. |
| `PointInTimeRef` | A point-in-time (PIT) token used for consistent pagination |

### Query DSL
| Type | Description |
|------|-------------|
| `QueryClause` | Union-style container for any query type (bool, term, match, range, geo, nested, knn, neural, etc.) |
| `BoolQuery` | Compound query with must, should, must_not, and filter clauses |
| `TermQuery` | Exact-value term query on a keyword or numeric field |
| `MatchQuery` | Full-text match query with fuzziness, operator, and analyzer options |
| `RangeQuery` | Range query supporting gte, gt, lte, lt with optional format and timezone |
| `GeoQuery` | Geospatial query (geo_distance, geo_bounding_box) with location and distance |
| `NestedQuery` | Query scoped to a nested object path with score mode |
| `KNNQuery` | k-nearest-neighbor vector search query with optional pre-filter |
| `NeuralQuery` | Semantic neural search query using an ML model for embedding generation |

### Aggregations
| Type | Description |
|------|-------------|
| `AggregationResult` | A named aggregation result that may contain buckets, a metric value, or raw output |
| `BucketResult` | A single bucket (term, date histogram, range, etc.) with doc count and sub-aggregations |
| `MetricResult` | A single-value or multi-value metric result (avg, sum, min, max, stats, percentiles, etc.) |

### Ingest
| Type | Description |
|------|-------------|
| `Pipeline` | An ingest pipeline with id, description, processors, and on-failure handlers |
| `PipelineDetails` | Version, processor list, and on-failure processor list |
| `Ingest` | Container for all pipelines and global ingest statistics |
| `IngestDetails` | Node-level ingest statistics including preprocessing time and per-pipeline stats |

### Cluster and nodes
| Type | Description |
|------|-------------|
| `Cluster` | Top-level cluster object with name, details, health, nodes, and settings |
| `ClusterDetails` | UUID, version, Lucene version, and wire/index compatibility versions |
| `ClusterHealth` | Status (green/yellow/red), shard counts, pending tasks, and in-flight fetch count |
| `NodeDetails` | Per-node information including roles, OS, JVM, thread pools, HTTP, and storage |
| `StorageInfo` | Total, free, and available disk bytes plus usage percentage |

### Snapshots
| Type | Description |
|------|-------------|
| `Snapshot` | A point-in-time backup of indices and data streams in a repository |
| `SnapshotDetails` | UUID, version, indices, state, start/end times, duration, shard results, and failures |

### Data streams
| Type | Description |
|------|-------------|
| `DataStream` | A time-series abstraction over rolling backing indices |
| `DataStreamDetails` | Timestamp field, generation counter, ILM policy, hidden/system/replicated flags |

### Index templates
| Type | Description |
|------|-------------|
| `Template` | A composable or legacy index template with patterns, mappings, settings, and aliases |
| `TemplateDetails` | Version, priority, composed-of component list, data stream config, and deprecation flag |

### Security (Security Plugin)
| Type | Description |
|------|-------------|
| `SecurityRole` | An OpenSearch security role with cluster and index-level permissions |
| `RolePermission` | Index permission entry with patterns, DLS filter, FLS fields, masked fields, and allowed actions |
| `User` | An internal user with backend roles, attributes, and description |
| `UserDetails` | Password hash, mapped roles, tenants, and legacy opendistro roles |
| `APIKey` | An API key with expiration, invalidation status, and metadata |
| `Token` | An authentication token (JWT-style) returned by the auth endpoint |

### Search Pipelines
| Type | Description |
|------|-------------|
| `SearchPipeline` | A named search pipeline applied at query time |
| `SearchPipelineDetails` | Version, description, request processors, response processors, and phase-result processors |

### ML Commons
| Type | Description |
|------|-------------|
| `MLModel` | A machine-learning model registered in the ML Commons plugin |
| `MLTask` | An asynchronous ML task (train, register, deploy, predict) with state and response |
| `MLConnector` | An external model connector (e.g., Bedrock, SageMaker, OpenAI) with protocol and credentials |

### k-NN
| Type | Description |
|------|-------------|
| `KNNIndex` | A k-NN vector field with engine config, dimension, and runtime statistics |

## Operations overview

### Query (read operations)

- Index: `index`, `indices`, `indexStats`, `indexMapping`, `indexSettings`, `indexAliases`
- Shards/segments: `shards`, `segments`
- Documents: `document`, `mget`
- Search: `search`, `msearch`, `explain`, `fieldCaps`, `rankEval`, `aggregations`
- Ingest: `pipeline`, `pipelines`, `ingestStats`
- Cluster: `cluster`, `clusterHealth`, `clusterSettings`, `nodes`, `nodeStats`
- Snapshots: `snapshot`, `snapshots`, `snapshotRepositories`, `snapshotStatus`
- Data streams: `dataStream`, `dataStreams`
- Templates: `template`, `templates`, `componentTemplate`, `componentTemplates`
- Security: `role`, `roles`, `user`, `users`, `apiKey`, `apiKeys`, `actionGroup`, `actionGroups`, `tenant`, `tenants`, `roleMapping`, `roleMappings`
- Search pipelines: `searchPipeline`, `searchPipelines`
- ML Commons: `mlModel`, `mlModels`, `mlTask`, `mlConnector`, `mlConnectors`
- k-NN: `knnIndex`, `knnIndices`, `knnWarmup`
- Cat APIs: `catIndices`, `catShards`, `catNodes`, `catHealth`, `catAliases`, `catTemplates`, `catSegments`, `catCount`, `catPendingTasks`

### Mutation (write operations)

- Index management: create, delete, close, open, clone, split, shrink, rollover, put mapping, put settings, put/delete alias, refresh, flush, forcemerge, clear cache
- Documents: index, update, delete, bulk, updateByQuery, deleteByQuery, reindex
- Ingest: create/delete/simulate pipeline
- Cluster: update settings, reroute shards, allocation explain
- Snapshots: create/delete repository, create/delete/restore/clone snapshot
- Data streams: create, delete, rollover
- Templates: put/delete index template, put/delete component template
- Security: create/update/delete users, roles, role mappings, action groups, tenants; create/invalidate API keys; change password; patch security config
- Search pipelines: create/delete search pipeline
- ML Commons: register, deploy, undeploy, delete, predict, train models; create/update/delete connectors

## Design notes

- All mutation inputs accept `JSON` scalars for the request body to mirror the OpenSearch REST API's flexible document model.
- Aggregation results are modeled with both `BucketResult` and `MetricResult` to cover the two major aggregation families; `raw: JSON` is provided as an escape hatch for complex nested aggregations.
- The `QueryClause` type intentionally mirrors the OpenSearch DSL union structure. In a production schema, each clause type would be split into separate input types per field.
- Authentication is assumed to be handled at the transport layer (Basic Auth, API key header, or JWT bearer token via the Security plugin).
- The ML Commons types cover the remote connector pattern used to invoke foundation models on AWS Bedrock, SageMaker, and third-party providers.
