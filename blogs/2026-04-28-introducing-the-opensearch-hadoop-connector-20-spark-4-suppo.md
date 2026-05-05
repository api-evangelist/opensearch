---
title: "Introducing the OpenSearch Hadoop connector 2.0: Spark 4 support, OpenSearch Serverless, and more"
url: "https://opensearch.org/blog/introducing-the-opensearch-hadoop-connector-2-0-spark-4-support-opensearch-serverless-and-more/"
date: "Tue, 28 Apr 2026 18:36:40 +0000"
author: "Sotaro Hikita"
feed_url: "https://opensearch.org/feed/"
---
<div class="wpb_row vc_row-fluid vc_row" id="fws_69f3c59dcce89" style="padding-top: 0px; padding-bottom: 0px;"><div class="row-bg-wrap"><div class="inner-wrap row-bg-layer"><div class="row-bg viewport-desktop"></div></div></div><div class="row_col_wrap_12 col span_12 dark left">
	<div class="vc_col-sm-12 wpb_column column_container vc_column_container col no-extra-padding inherit_tablet inherit_phone flex_gap_desktop_10px ">
		<div class="vc_column-inner">
			<div class="wpb_wrapper">
				
<div class="wpb_text_column wpb_content_element ">
	<p>We&#8217;re excited to announce the release of the OpenSearch Hadoop connector 2.0. Key updates include Apache Spark 3.5 and 4 support, OpenSearch 3.x compatibility, Amazon OpenSearch Serverless support, and more.</p>
<p>We&#8217;ve also published new <a href="https://docs.opensearch.org/latest/clients/hadoop/" rel="nofollow">Hadoop connector documentation</a> that describes setup, usage examples, and configuration options. This post introduces the Hadoop connector and describes the new features in version 2.0.</p>
<p><strong>TL;DR:</strong> OpenSearch Hadoop connector 2.0 adds Spark 3.5 and 4 support, OpenSearch 3.x compatibility, and Amazon OpenSearch Serverless integration. The connector parallelizes reads and writes across Spark partitions and OpenSearch shards for efficient large-scale data processing.</p>
<h2>What is the Hadoop connector?</h2>
<p>The <a href="https://github.com/opensearch-project/opensearch-hadoop">Hadoop connector</a> enables reading and writing data between <a href="https://spark.apache.org/" rel="nofollow">Apache Spark</a>, <a href="https://hive.apache.org/" rel="nofollow">Apache Hive</a>, <a href="https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html" rel="nofollow">Hadoop MapReduce</a>, and OpenSearch. Because these systems are distributed, the connector parallelizes reads and writes across compute partitions and OpenSearch shards, enabling efficient processing of large data volumes, as shown in the following image.</p>
<p><img alt="" class="aligncenter wp-image-10167 size-full" height="1942" src="https://opensearch.org/wp-content/uploads/2026/04/opensearch-hadoop-architecture-scaled.png" width="2560" /></p>
<h2>What&#8217;s new in Hadoop connector 2.0</h2>
<p>The 2.0 release brings the following major features and improvements.</p>
<h3>Apache Spark 3.5 and 4 support</h3>
<p>The Hadoop connector 2.0 introduces dedicated modules for Spark 3.5 and Spark 4 alongside the existing Spark 3.4 module. Choose the artifact that matches your Spark and Scala version.</p>
<table>
<thead>
<tr>
<th>Spark version</th>
<th>Scala version</th>
<th>Artifact</th>
</tr>
</thead>
<tbody>
<tr>
<td>3.4.x</td>
<td>2.12</td>
<td><code>org.opensearch.client:opensearch-spark-30_2.12:2.0.0</code></td>
</tr>
<tr>
<td>3.4.x</td>
<td>2.13</td>
<td><code>org.opensearch.client:opensearch-spark-30_2.13:2.0.0</code></td>
</tr>
<tr>
<td>3.5.x</td>
<td>2.12</td>
<td><code>org.opensearch.client:opensearch-spark-35_2.12:2.0.0</code></td>
</tr>
<tr>
<td>3.5.x</td>
<td>2.13</td>
<td><code>org.opensearch.client:opensearch-spark-35_2.13:2.0.0</code></td>
</tr>
<tr>
<td>4.x</td>
<td>2.13</td>
<td><code>org.opensearch.client:opensearch-spark-40_2.13:2.0.0</code></td>
</tr>
</tbody>
</table>
<p>The Spark 3.5 module lets you use the connector on platforms that include Spark 3.5. The Spark 4 module brings support for the latest Spark release, including Spark 4.0 and 4.1, so you can take advantage of the newest Spark features while reading and writing data to OpenSearch.</p>
<p>To try the connector with Spark 4, launch a PySpark shell with the connector loaded using <code>--packages</code>:</p>
<pre>pyspark --packages org.opensearch.client:opensearch-spark-40_2.13:2.0.0</pre>
<p>Then write and read data:</p>
<pre><span class="pl-c rich-diff-level-one"># Write documents to OpenSearch</span>
<span class="pl-s1 rich-diff-level-one">df</span> <span class="pl-c1 rich-diff-level-one">=</span> <span class="pl-s1 rich-diff-level-one">spark</span>.<span class="pl-c1 rich-diff-level-one">createDataFrame</span>([(<span class="pl-s rich-diff-level-one">"John"</span>, <span class="pl-c1 rich-diff-level-one">30</span>), (<span class="pl-s rich-diff-level-one">"Jane"</span>, <span class="pl-c1 rich-diff-level-one">25</span>)], [<span class="pl-s rich-diff-level-one">"name"</span>, <span class="pl-s rich-diff-level-one">"age"</span>])
<span class="pl-s1 rich-diff-level-one">df</span>.<span class="pl-c1 rich-diff-level-one">write</span>.<span class="pl-c1 rich-diff-level-one">format</span>(<span class="pl-s rich-diff-level-one">"opensearch"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.nodes"</span>, <span class="pl-s rich-diff-level-one">"&lt;opensearch host&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.port"</span>, <span class="pl-s rich-diff-level-one">"&lt;port&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">save</span>(<span class="pl-s rich-diff-level-one">"people"</span>)

<span class="pl-c rich-diff-level-one"># Read documents from OpenSearch</span>
<span class="pl-s1 rich-diff-level-one">df</span> <span class="pl-c1 rich-diff-level-one">=</span> <span class="pl-s1 rich-diff-level-one">spark</span>.<span class="pl-c1 rich-diff-level-one">read</span>.<span class="pl-c1 rich-diff-level-one">format</span>(<span class="pl-s rich-diff-level-one">"opensearch"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.nodes"</span>, <span class="pl-s rich-diff-level-one">"&lt;opensearch host&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.port"</span>, <span class="pl-s rich-diff-level-one">"&lt;port&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">load</span>(<span class="pl-s rich-diff-level-one">"people"</span>)
<span class="pl-s1 rich-diff-level-one">df</span>.<span class="pl-c1 rich-diff-level-one">show</span>()</pre>
<p>You can also push queries down to OpenSearch so that only matching documents are transferred to Spark:</p>
<pre><span class="pl-s1 rich-diff-level-one">filtered</span> <span class="pl-c1 rich-diff-level-one">=</span> <span class="pl-s1 rich-diff-level-one">spark</span>.<span class="pl-c1 rich-diff-level-one">read</span> \
    .<span class="pl-c1 rich-diff-level-one">format</span>(<span class="pl-s rich-diff-level-one">"opensearch"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.nodes"</span>, <span class="pl-s rich-diff-level-one">"&lt;opensearch host&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.port"</span>, <span class="pl-s rich-diff-level-one">"&lt;port&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.query"</span>, <span class="pl-s rich-diff-level-one">'{"query":{"match":{"name":"John"}}}'</span>) \
    .<span class="pl-c1 rich-diff-level-one">load</span>(<span class="pl-s rich-diff-level-one">"people"</span>)
<span class="pl-s1 rich-diff-level-one">filtered</span>.<span class="pl-c1 rich-diff-level-one">show</span>()</pre>
<p>For authentication options and Scala, Java, and Spark SQL examples, see the <a href="https://docs.opensearch.org/latest/clients/hadoop/" rel="nofollow">Hadoop connector documentation</a>.</p>
<h3>Amazon OpenSearch Serverless support</h3>
<p>You can now use the connector with <a href="https://docs.aws.amazon.com/opensearch-service/latest/developerguide/serverless.html" rel="nofollow">Amazon OpenSearch Serverless</a> collections. Configure the connector with AWS Signature Version 4 authentication and the <code>aoss</code> service name:</p>
<pre><span class="pl-s1 rich-diff-level-one">df</span> <span class="pl-c1 rich-diff-level-one">=</span> <span class="pl-s1 rich-diff-level-one">spark</span>.<span class="pl-c1 rich-diff-level-one">createDataFrame</span>([(<span class="pl-s rich-diff-level-one">"product-1"</span>, <span class="pl-c1 rich-diff-level-one">29.99</span>), (<span class="pl-s rich-diff-level-one">"product-2"</span>, <span class="pl-c1 rich-diff-level-one">49.99</span>)], [<span class="pl-s rich-diff-level-one">"name"</span>, <span class="pl-s rich-diff-level-one">"price"</span>])
<span class="pl-s1 rich-diff-level-one">df</span>.<span class="pl-c1 rich-diff-level-one">write</span>.<span class="pl-c1 rich-diff-level-one">format</span>(<span class="pl-s rich-diff-level-one">"opensearch"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.nodes"</span>, <span class="pl-s rich-diff-level-one">"https://&lt;collection-id&gt;.&lt;region&gt;.aoss.amazonaws.com"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.port"</span>, <span class="pl-s rich-diff-level-one">"443"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.nodes.wan.only"</span>, <span class="pl-s rich-diff-level-one">"true"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.net.ssl"</span>, <span class="pl-s rich-diff-level-one">"true"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.aws.sigv4.enabled"</span>, <span class="pl-s rich-diff-level-one">"true"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.aws.sigv4.region"</span>, <span class="pl-s rich-diff-level-one">"&lt;region&gt;"</span>) \
    .<span class="pl-c1 rich-diff-level-one">option</span>(<span class="pl-s rich-diff-level-one">"opensearch.aws.sigv4.service"</span>, <span class="pl-s rich-diff-level-one">"aoss"</span>) \
    .<span class="pl-c1 rich-diff-level-one">save</span>(<span class="pl-s rich-diff-level-one">"my-collection"</span>)</pre>
<h3>OpenSearch 3.x compatibility</h3>
<p>Because the connector communicates with OpenSearch through its REST API, it already worked with OpenSearch 3.x. This release updates the build and test infrastructure to officially support OpenSearch 3.x clusters.</p>
<h2>Other notable changes</h2>
<p>This release includes the following additional changes:</p>
<ul>
<li>The legacy Spark 2.x module has been removed.</li>
<li>The AWS authentication layer has been migrated from AWS SDK v1 to v2, bringing support for newer credential providers and aligning with the AWS SDK v1 end-of-maintenance timeline.</li>
<li>The minimum runtime JDK has been raised from 8 to 11, and the minimum build JDK is now 21.</li>
<li>Various bug fixes have improved overall stability. For the full list of changes, see the <a href="https://github.com/opensearch-project/opensearch-hadoop/blob/main/CHANGELOG.md">CHANGELOG</a>.</li>
</ul>
<h2>Getting started</h2>
<p>Use the following resources to get started with the Hadoop connector 2.0:</p>
<ul>
<li>To download the Hadoop connector, see the <a href="https://central.sonatype.com/search?q=org.opensearch.client%20opensearch-spark" rel="nofollow">Maven Central artifacts</a>.</li>
<li>For usage examples and configuration options, see the <a href="https://docs.opensearch.org/latest/clients/hadoop/" rel="nofollow">Hadoop connector documentation</a>.</li>
<li>To learn more about the project, see the <a href="https://github.com/opensearch-project/opensearch-hadoop">Hadoop connector repository</a>.</li>
</ul>
<p>We welcome your feedback about this release. If you have questions or suggestions, please visit the <a href="https://forum.opensearch.org/" rel="nofollow">community forum</a> or open an issue on <a href="https://github.com/opensearch-project/opensearch-hadoop/issues">GitHub</a>.</p>
</div>




			</div> 
		</div>
	</div> 
</div></div>
<p>The post <a href="https://opensearch.org/blog/introducing-the-opensearch-hadoop-connector-2-0-spark-4-support-opensearch-serverless-and-more/">Introducing the OpenSearch Hadoop connector 2.0: Spark 4 support, OpenSearch Serverless, and more</a> appeared first on <a href="https://opensearch.org">OpenSearch</a>.</p>
