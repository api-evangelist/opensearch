---
title: "Benchmarking multimodal document search in OpenSearch: Three approaches compared"
url: "https://opensearch.org/blog/benchmarking-multimodal-document-search-in-opensearch-three-approaches-compared/"
date: "Tue, 21 Apr 2026 18:11:54 +0000"
author: "Nate Po Hong Lau"
feed_url: "https://opensearch.org/feed/"
---
<div class="wpb_row vc_row-fluid vc_row" id="fws_69f3c59dd8132" style="padding-top: 0px; padding-bottom: 0px;"><div class="row-bg-wrap"><div class="inner-wrap row-bg-layer"><div class="row-bg viewport-desktop"></div></div></div><div class="row_col_wrap_12 col span_12 dark left">
	<div class="vc_col-sm-12 wpb_column column_container vc_column_container col no-extra-padding inherit_tablet inherit_phone flex_gap_desktop_10px ">
		<div class="vc_column-inner">
			<div class="wpb_wrapper">
				
<div class="wpb_text_column wpb_content_element ">
	<p>Many real-world documents—financial filings, research papers, technical reports—contain more than just text. They include tables, charts, diagrams, and images that carry critical information. Traditional text-based search does not capture this visual content.</p>
<p>To solve this problem, OpenSearch supports multimodal document search, which is implemented using vector search and neural search pipelines. However, there are multiple approaches to indexing and querying multimodal data, each with different trade-offs in search quality, latency, and complexity.</p>
<p>To help you find the approach that best fits your use case, we benchmarked three approaches on the same dataset of 1,000 report pages. This blog post describes each approach, presents the benchmarking results, and explains when to use each one.</p>
<p class="qs:text-body-default qs:leading-snug qs:!mb-4 qs:!mt-0"><strong>TL;DR:</strong> Three multimodal search approaches benchmarked on 1,000 report pages in OpenSearch.</p>
<ul class="qs:text-body-default">
<li class="qs:text-body-default">ColPali leads in quality with 92% recall but highest latency</li>
<li class="qs:text-body-default">BDA modality-aware embedding balances quality and speed</li>
<li class="qs:text-body-default">Text-only chunking is simplest but misses visual content</li>
<li class="qs:text-body-default">Documents with charts, tables, and diagrams need multimodal search</li>
<li class="qs:text-body-default">Text-only approaches fail when visual elements carry the answer</li>
<li class="qs:text-body-default">Choose based on quality vs. latency priorities</li>
</ul>
<h2>Dataset</h2>
<p>We used the <a href="https://huggingface.co/datasets/vidore/syntheticDocQA_government_reports_test" rel="nofollow">vidore/syntheticDocQA_government_reports_test</a> dataset from Hugging Face for benchmarking. This dataset contains 1,000 scanned report pages with 100 query-answer pairs. Each query has a single relevant document, making it a clean retrieval benchmark.</p>
<h2>Three approaches compared</h2>
<p>We evaluated the following three approaches, each representing a different point on the quality-latency spectrum.</p>
<h3>Approach 1: ColPali late interaction reranking</h3>
<p>ColPali is a vision-language model that treats each document page as an image and produces multiple patch-level embeddings (a <em>late interaction</em> approach). At search time, the query is also encoded into multiple token embeddings and relevance is computed by comparing every query token against every document patch. This is similar to how ColBERT works for text, but extended to visual content.</p>
<p>The following diagram shows the ColPali process:</p>
<pre><code>Document image → SageMaker GPU endpoint (ColPali model) → multiple patch embeddings stored in OpenSearch → at search time, query embeddings compared against all patch embeddings via late interaction scoring.
</code></pre>
<p>This approach processes the entire page (including text, tables, charts, and layout) as a single image, without requiring any text extraction or parsing.</p>
<h3>Approach 2: BDA modality-aware embedding</h3>
<p>This approach uses Amazon Bedrock Data Automation (BDA) to parse each document into typed elements: paragraphs, tables, and figures. Each element is then embedded separately using Amazon Titan Multimodal Embeddings: text elements use the text modality and figures use the image modality (cropped from the original page using bounding box coordinates). All embeddings are stored in the same 1,024-dimensional vector space.</p>
<p>The following diagram shows the BDA process:</p>
<pre><code>Document → BDA parsing → element extraction (PARAGRAPH, TABLE, FIGURE) → Titan text embedding for text elements, Titan image embedding for figure elements → all stored as nested documents in OpenSearch → neural search at query time.
</code></pre>
<p>This approach preserves modality-specific information. For example, a chart is embedded as an image, not as Optical Character Recognition (OCR) text.</p>
<h3>Approach 3: Text-only chunking</h3>
<p>Text-only chunking is the simplest approach, which represents a common pattern in practice. First, BDA extracts raw text from the document. Then the text is chunked into ~200-word segments with 30-word overlap and each chunk is embedded using Amazon Titan Text Embeddings models.</p>
<p>The following diagram shows the text-only chunking process:</p>
<pre><code>Document image → BDA text extraction → chunk into ~200-word segments → Titan text embedding per chunk → stored as nested documents in OpenSearch → neural search at query time.
</code></pre>
<p>This approach is straightforward to implement but discards all visual information: tables become flattened text while charts, diagrams, and other visual elements are ignored entirely.</p>
<h2>Benchmarking configuration</h2>
<p>To ensure a fair comparison, we controlled the following variables during benchmarking.</p>
<table>
<thead>
<tr>
<th>Variable</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr>
<td>Dataset</td>
<td>Same 1,000 report pages</td>
</tr>
<tr>
<td>Queries</td>
<td>Same 100 queries with ground-truth relevance</td>
</tr>
<tr>
<td>OpenSearch cluster</td>
<td>Same local cluster (OpenSearch 3.5.0)</td>
</tr>
<tr>
<td>Evaluation metrics</td>
<td>NDCG, MRR, Recall at k=5 and k=10</td>
</tr>
<tr>
<td>Execution</td>
<td>Interleaved (queries rotated across approaches to avoid ordering bias)</td>
</tr>
<tr>
<td>Warmup</td>
<td>3 warmup queries per approach before measurement</td>
</tr>
</tbody>
</table>
<h2>Metric definitions</h2>
<p>We used the following metrics to evaluate search quality and performance:</p>
<ul>
<li><strong>NDCG@k (Normalized Discounted Cumulative Gain)</strong>: Measures how well relevant results are ranked near the top. A score of 1.0 indicates perfect ranking. @5 and @10 indicate evaluation over the top 5 or 10 results.</li>
<li><strong>MRR@k (Mean Reciprocal Rank)</strong>: Measures how quickly the first relevant result appears. A score of 1.0 means the correct document is always ranked first.</li>
<li><strong>Recall@k</strong>: Measures the percentage of relevant documents retrieved in the top <em>k</em> results.</li>
<li><strong>Latency (ms)</strong>: Indicates the average search response time per query, in milliseconds.</li>
<li><strong>P95 latency (ms)</strong>: Indicates the 95th percentile response time: 95% of queries complete faster than this value.</li>
</ul>
<h2>Search quality results</h2>
<p>The following table compares the three approaches across search quality metrics and query latency.</p>
<table>
<thead>
<tr>
<th>Approach</th>
<th>NDCG@5</th>
<th>NDCG@10</th>
<th>MRR@5</th>
<th>Recall@5</th>
<th>Recall@10</th>
<th>Latency (ms)</th>
<th>P95 (ms)</th>
</tr>
</thead>
<tbody>
<tr>
<td>ColPali late interaction reranking</td>
<td>0.77</td>
<td>0.77</td>
<td>0.72</td>
<td>0.92</td>
<td>0.92</td>
<td>1,683</td>
<td>1,969</td>
</tr>
<tr>
<td>BDA modality-aware embedding</td>
<td>0.51</td>
<td>0.54</td>
<td>0.45</td>
<td>0.69</td>
<td>0.77</td>
<td>257</td>
<td>306</td>
</tr>
<tr>
<td>Text-only chunking</td>
<td>0.38</td>
<td>0.42</td>
<td>0.33</td>
<td>0.52</td>
<td>0.64</td>
<td>294</td>
<td>370</td>
</tr>
</tbody>
</table>
<p>ColPali leads across every quality metric. With an NDCG@10 of 0.77 and Recall@10 of 0.92, it finds the correct document 92% of the time within the top 10 results, and the high NDCG@10 score indicates that relevant documents tend to appear in the higher positions. The trade-off is latency: at ~1,683 ms per query, ColPali is roughly 6–7x slower than the other two approaches because late interaction scoring compares query token embeddings against all stored patch embeddings and the reranking step runs on a SageMaker GPU endpoint.</p>
<p>The BDA modality-aware embedding approach falls between the other two, offering moderate search quality (NDCG@10 = 0.54) with low latency (~257 ms). By preserving images and tables as separate modalities, it captures information that text-only approaches miss.</p>
<p>Text-only chunking is the fastest to implement but scores lowest (NDCG@10 = 0.42). When documents contain tables, charts, or diagrams that carry the answer, a text-only approach cannot retrieve them.</p>
<h2>Ingest latency results</h2>
<p>We also measured how long it takes to ingest each document (50-document sample). The following table shows the results of the benchmarking tests.</p>
<table>
<thead>
<tr>
<th>Approach</th>
<th>Mean (s/doc)</th>
<th>Median (s/doc)</th>
<th>P95 (s/doc)</th>
</tr>
</thead>
<tbody>
<tr>
<td>ColPali late interaction reranking</td>
<td>9.0</td>
<td>9.1</td>
<td>10.0</td>
</tr>
<tr>
<td>BDA modality-aware embedding</td>
<td>5.1</td>
<td>5.0</td>
<td>6.9</td>
</tr>
<tr>
<td>Text-only chunking</td>
<td>11.0</td>
<td>6.5</td>
<td>21.7</td>
</tr>
</tbody>
</table>
<p>The BDA modality-aware embedding approach has the most consistent and fastest ingest times. ColPali late interaction reranking is steady at ~9 seconds per document, driven by the Amazon SageMaker GPU inference time. Text-only chunking has the highest variance: the median is 6.5 seconds, but the P95 increases to 21.7 seconds because some documents produce many text chunks, each requiring a separate embedding call.</p>
<h2>Which approach should you choose?</h2>
<p>The best approach depends on your documents and your priorities:</p>
<ul>
<li><strong>ColPali late interaction reranking</strong>: Choose this approach if search quality is your top priority and you can tolerate higher search latency. It&#8217;s the best option when documents are visually rich (charts, diagrams, complex layouts) and accuracy matters more than speed. This approach requires a GPU endpoint (for example, Amazon SageMaker).</li>
<li><strong>BDA modality-aware embedding</strong>: Choose this approach if you want a balance of quality and low latency. It handles mixed-content documents well by treating text and images as separate modalities. This approach provides a suitable balance for most use cases.</li>
<li><strong>Text-only chunking</strong>: Choose this approach if your documents are primarily text-based, or if simplicity and fast implementation are priorities. It&#8217;s the easiest to set up but will underperform on documents where visual elements carry important information.</li>
</ul>
<h2>Next steps</h2>
<p>To learn more about vector search and neural search in OpenSearch, see the following resources:</p>
<ul>
<li><a href="https://docs.opensearch.org/latest/search-plugins/neural-multimodal-search/" rel="nofollow">Multimodal search</a></li>
<li><a href="https://docs.opensearch.org/latest/search-plugins/search-relevance/rerank-by-field-late-interaction/" rel="nofollow">Reranking by a field using an externally hosted late interaction model</a></li>
</ul>
<p>Have questions or want to share your own benchmarking results? Join the conversation on the <a href="https://forum.opensearch.org/" rel="nofollow">OpenSearch forum</a>.</p>
</div>




			</div> 
		</div>
	</div> 
</div></div>
<p>The post <a href="https://opensearch.org/blog/benchmarking-multimodal-document-search-in-opensearch-three-approaches-compared/">Benchmarking multimodal document search in OpenSearch: Three approaches compared</a> appeared first on <a href="https://opensearch.org">OpenSearch</a>.</p>
