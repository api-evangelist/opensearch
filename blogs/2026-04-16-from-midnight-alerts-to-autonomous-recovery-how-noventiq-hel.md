---
title: "From Midnight Alerts to Autonomous Recovery: How Noventiq Helped Build Self-Healing Infrastructure"
url: "https://opensearch.org/case-studies/from-midnight-alerts-to-autonomous-recovery-how-noventiq-helped-build-self-healing-infrastructure/"
date: "Thu, 16 Apr 2026 07:00:17 +0000"
author: "Lisa Briggs"
feed_url: "https://opensearch.org/feed/"
---
<div class="wpb_row vc_row-fluid vc_row" id="fws_69f3c59de40c9" style="padding-top: 0px; padding-bottom: 0px;"><div class="row-bg-wrap"><div class="inner-wrap row-bg-layer"><div class="row-bg viewport-desktop"></div></div></div><div class="row_col_wrap_12 col span_12 dark left">
	<div class="vc_col-sm-12 wpb_column column_container vc_column_container col no-extra-padding inherit_tablet inherit_phone flex_gap_desktop_10px ">
		<div class="vc_column-inner">
			<div class="wpb_wrapper">
				
	<div class="wpb_video_widget wpb_content_element vc_clearfix   vc_video-aspect-ratio-169 vc_video-el-width-70 vc_video-align-center">
		<div class="wpb_wrapper">
			
			<div class="wpb_video_wrapper"></div>
		</div>
	</div>

<div class="wpb_text_column wpb_content_element ">
	<h3><b>High-Level Executive Summary</b></h3>
<p><span style="font-weight: 400;">At a major enterprise scale, infrastructure teams were struggling with alert fatigue, slow incident response, and fragmented operational knowledge. Led by Dzung Le at Noventiq, the team implemented a self-healing infrastructure model using agentic AI and vector search in OpenSearch. This approach reduced manual intervention, improved resolution times, and laid the groundwork for autonomous operations while maintaining critical human oversight.</span></p>
<h2><b>Challenge</b></h2>
<p><span style="font-weight: 400;">Infrastructure operations had reached a breaking point.</span></p>
<p><span style="font-weight: 400;">Despite advanced observability systems, engineers were still required to manually investigate and resolve incidents, often at inconvenient hours. Many issues were simple to fix but time-consuming to diagnose.</span></p>
<p><span style="font-weight: 400;">Key challenges included:</span></p>
<ul>
<li style="font-weight: 400;"><b>Alert fatigue</b><span style="font-weight: 400;"> from excessive monitoring noise</span></li>
<li style="font-weight: 400;"><b>High mean time to resolution (MTTR)</b><span style="font-weight: 400;"> due to manual log analysis</span></li>
<li style="font-weight: 400;"><b>Tribal knowledge dependency</b><span style="font-weight: 400;">, with fixes buried in tickets or individual expertise</span></li>
<li style="font-weight: 400;"><b>Customer impact</b><span style="font-weight: 400;">, especially in systems serving millions of users</span></li>
</ul>
<p><span style="font-weight: 400;">“We have built systems that are great at yelling at us when they break, but they have no idea of how to fix themselves.”</span></p>
<p><span style="font-weight: 400;">In one banking-scale deployment supporting over 7 million users, even minor disruptions in AI-driven services could significantly impact user experience and business outcomes.</span></p>
<h2><b>Solution</b></h2>
<p><span style="font-weight: 400;">Under the guidance of Dzung Le, the team designed a </span><b>self-healing infrastructure architecture</b><span style="font-weight: 400;"> combining agentic AI with vector search capabilities in OpenSearch.</span></p>
<h3><b>Core Components</b></h3>
<p><b>Agentic AI System</b></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Moves beyond chatbots to autonomous agents</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Capable of reasoning, planning, and executing actions</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Structured as:</span>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Brain: LLM for decision-making</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Eyes: OpenSearch for observability</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Hands: Execution layer for remediation</span></li>
</ul>
</li>
</ul>
<p><b>Vector Search with OpenSearch</b></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Transforms logs, runbooks, and incidents into semantic embeddings</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Enables contextual matching between errors and solutions</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Eliminates reliance on exact keyword matches</span></li>
</ul>
<p><b>Retrieval-Augmented Generation (RAG)</b></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Anchors AI decisions in real operational data</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Ensures recommendations are based on verified runbooks</span></li>
</ul>
<p><b>Multi-Agent Orchestration</b></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Specialized agents for monitoring, investigation, and remediation</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Central orchestrator coordinates workflows</span></li>
</ul>
<p><b>Human-in-the-Loop Safeguards</b></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Automates low-risk fixes (service restarts, cache clearing)</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Requires approval for high-risk actions (database changes, traffic routing)</span></li>
</ul>
<h3><b>How It Works</b></h3>
<p><span style="font-weight: 400;">The system operates as a continuous self-healing loop:</span></p>
<ol>
<li style="font-weight: 400;"><span style="font-weight: 400;">Detect anomalies through monitoring systems</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Investigate logs automatically via OpenSearch</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Retrieve similar incidents using vector search</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Generate root cause analysis and recommended fix</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Execute remediation with optional human approval</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Store outcomes to continuously improve the knowledge base</span></li>
</ol>
<h2><b>Results</b></h2>
<p><span style="font-weight: 400;">The implementation delivered tangible improvements across operations:</span></p>
<ul>
<li style="font-weight: 400;"><b>Faster incident resolution</b><span style="font-weight: 400;"> by automating investigation and diagnosis</span></li>
<li style="font-weight: 400;"><b>Reduced operational load</b><span style="font-weight: 400;">, minimizing manual intervention and late-night escalations</span></li>
<li style="font-weight: 400;"><b>Improved knowledge accessibility</b><span style="font-weight: 400;">, converting static runbooks into a living AI-driven system</span></li>
<li style="font-weight: 400;"><b>Increased system resilience</b><span style="font-weight: 400;"> through multi-model AI and failover strategies</span></li>
</ul>
<p><span style="font-weight: 400;">“AI will not replace humans, but humans using AI will replace humans who don’t.”</span></p>
<h2><b>Why It Matters</b></h2>
<p><span style="font-weight: 400;">This approach represents a shift from reactive infrastructure management to </span><b>autonomous, intelligent operations</b><span style="font-weight: 400;">.</span></p>
<p><span style="font-weight: 400;">Instead of systems that only alert humans, organizations can build systems that:</span></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Understand issues in context</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Learn from past incidents</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Take action safely and efficiently</span></li>
</ul>
<p><span style="font-weight: 400;">For enterprises operating at scale, this is the difference between constant firefighting and sustainable reliability.</span></p>
<h2><b>Call to Action</b></h2>
<p><span style="font-weight: 400;">To start building self-healing infrastructure:</span></p>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Centralize your logs, metrics, and runbooks in OpenSearch</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Implement vector search to unlock semantic understanding</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Introduce agentic AI with strict human-in-the-loop controls</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Begin with low-risk automation and scale gradually</span></li>
</ul>
<h2><b>Learn more:</b></h2>
<ul>
<li style="font-weight: 400;"><a href="https://opensearch.org/case-studies/from-midnight-alerts-to-autonomous-recovery-how-noventiq-helped-build-self-healing-infrastructure/"><span style="font-weight: 400;">Explore the full talk.</span></a></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Discover <a href="https://noventiq.com/">Noventiq</a> solutions and services</span></li>
</ul>
</div>




			</div> 
		</div>
	</div> 
</div></div>
<p>The post <a href="https://opensearch.org/case-studies/from-midnight-alerts-to-autonomous-recovery-how-noventiq-helped-build-self-healing-infrastructure/">From Midnight Alerts to Autonomous Recovery: How Noventiq Helped Build Self-Healing Infrastructure</a> appeared first on <a href="https://opensearch.org">OpenSearch</a>.</p>
