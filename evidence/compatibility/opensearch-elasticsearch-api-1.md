<!-- fetched 2026-10-13 from https://docs.opensearch.org/latest/clients/ by sweep-shape-compat.py; text extracted from the provider's own page -->

OpenSearch language clients | OpenSearch Documentation Search Menu Expand Document Documentation Menu OpenSearch Menu 
 About 
 Releases 
 Roadmap 
 FAQ 
 Platform 
 Search 
 Observability 
 Security Analytics 
 Vector Database 
 Playground Demo 
 Performance Benchmarks 
 Community 
 Forum 
 Slack 
 Events 
 Solutions Providers 
 Projects 
 Members 
 Documentation 
 OpenSearch and Dashboards 
 Data Prepper 
 Clients 
 Benchmark 
 Migration Assistant 
 Blog 
 Download 
 Documentation 
 OpenSearch clients ← Back to docs home 
 Python client Python ML client 
 Java client 
 JavaScript client Helper methods 
 Go client 
 Ruby client 
 PHP client 
 .NET clients Getting started with the high-level .NET client 
 More advanced features of the high-level .NET client 
 .NET client considerations 
 Low-level .NET client 
 Rust client 
 Hadoop connector 
 Java high-level REST client (deprecated) 
 High-level Python client (deprecated) 
 OpenSearch language clients
 OpenSearch clients let you work with OpenSearch from your application code. A client connects to your cluster, sends requests, and returns the responses as objects in your programming language, so you can create indexes, add documents, and search without building HTTP requests and parsing JSON yourself.
 OpenSearch clients
 OpenSearch provides clients for the following programming languages and platforms:
 Python OpenSearch Python client 
 OpenSearch Python ML client : Analyze data in OpenSearch indexes using DataFrames and upload machine learning (ML) models to OpenSearch.
 Java OpenSearch Java client 
 JavaScript OpenSearch JavaScript (Node.js) client 
 Go OpenSearch Go client 
 Ruby OpenSearch Ruby client 
 PHP OpenSearch PHP client 
 .NET OpenSearch .NET clients 
 Rust OpenSearch Rust client 
 Hadoop Hadoop connector (Apache Spark, Apache Hive, and Hadoop MapReduce) 
 Deprecated clients
 The following clients have been deprecated:
 OpenSearch high-level Python client : Use the OpenSearch Python client instead.
 OpenSearch Java high-level REST client : Use the OpenSearch Java client instead.
 Legacy clients
 Clients that work with Elasticsearch OSS 7.10.2 should work with OpenSearch 1.x. The latest versions of those clients, however, might include license or version checks that artificially break compatibility. The following table provides recommendations for which client versions to use for best compatibility with OpenSearch 1.x. For OpenSearch 2.0 and later, no Elasticsearch clients are fully compatible with OpenSearch.
 While OpenSearch and Elasticsearch share several core features, mixing and matching the client and server has a high risk of errors and unexpected results. As OpenSearch and Elasticsearch continue to diverge, such risks may increase. Although your Elasticsearch client may continue working with your OpenSearch cluster, using OpenSearch clients for OpenSearch clusters is recommended.
 To view the compatibility matrix for a specific client, see the COMPATIBILITY.md file in the client’s repository.
 Client | Recommended version | 
 Elasticsearch Java low-level REST client | 7.13.4 | 
 Elasticsearch Java high-level REST client | 7.13.4 | 
 Elasticsearch Python client | 7.13.4 | 
 Elasticsearch Node.js client | 7.13.0 | 
 Elasticsearch Ruby client | 7.13.0 | 
 If you test a legacy client and verify that it works, submit a PR and add it to this table.
 OpenSearch clients 
 Deprecated clients 
 Legacy clients 
 WAS THIS PAGE HELPFUL?
 ✔ Yes ✖ No 
 Tell us why
 350 characters left
 Send Thank you for your feedback!
 Have a question? Ask us on the OpenSearch forum .
 Want to contribute? Edit this page or create an issue .
 OpenSearch Links
 Get Involved
 Code of Conduct 
 Forum 
 GitHub 
 Slack 
 Resources
 About 
 Release Schedule 
 Maintenance Policy 
 FAQ 
 Testimonials 
 Trademark and Brand Policy 
 Privacy 
 Contact Us
 Connect 
 Twitter 
 LinkedIn 
 YouTube 
 Meetup 
 Facebook 
 Copyright © OpenSearch Project a Series of LF Projects, LLC
 For web site terms of use, trademark policy and other project policies please see https://lfprojects.org .
