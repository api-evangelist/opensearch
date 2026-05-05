---
title: "Solving context overflow: How OpenSearch agents stay smart in long conversations"
url: "https://opensearch.org/blog/solving-context-overflow-how-opensearch-agents-stay-smart-in-long-conversations/"
date: "Mon, 13 Apr 2026 17:16:35 +0000"
author: "Mingshi Liu"
feed_url: "https://opensearch.org/feed/"
---
<p>&nbsp;</p>
<p>As AI agents become more sophisticated and handle longer conversations with multiple tool interactions, managing context efficiently becomes critical. Today, we&#8217;re excited to introduce <em class="rich-diff-level-one">context management</em> for OpenSearch Agents in OpenSearch 3.5.</p>
<h2>The problem: Context window overflow</h2>
<p>Modern AI agents face a fundamental challenge: context window limitations. As your agents engage in lengthy conversations, use multiple tools, and accumulate interaction history, they quickly approach token limits. When context exceeds LLM limits, requests fail. As context becomes unwieldy, performance degrades. Processing unnecessary tokens increases costs, and when irrelevant context confuses the model, hallucinations increase.</p>
<p>Traditional approaches to this problem are crude and involve cutting off old messages by token limit. But this loses valuable context and breaks your agent&#8217;s ability to maintain coherent, long-running conversations.</p>
<h2>The solution: Intelligent context engineering</h2>
<p>Context management introduces a sophisticated hook-based system that allows you to engineer your agent&#8217;s context dynamically. Your agents can now intelligently summarize older interactions while preserving key information, apply sliding windows to maintain recent context, truncate tool outputs strategically when they become too large, and combine multiple strategies for optimal context optimization.</p>
<h2>How context management works</h2>
<p>Context management operates through a hook-based architecture that intercepts agent execution at specific points. The <code class="rich-diff-level-one">pre_llm</code> hook optimizes context before sending requests to the LLM, while the <code class="rich-diff-level-one">post_tool</code> hook processes context after tool execution completes. At each hook, you can configure teams of context managers that work together to optimize your agent&#8217;s context.</p>
<h3>Context managers</h3>
<p>One of the most powerful aspects of context management is its flexibility. You can mix and match different context managers, adjust parameters to fit your specific use case, experiment with thresholds to find optimal performance, and combine strategies for comprehensive context optimization. Start with conservative settings and gradually adjust based on your agent&#8217;s performance and requirements.</p>
<p>OpenSearch provides three built-in context managers.</p>
<h4>Sliding window manager</h4>
<p>The <em class="rich-diff-level-one">sliding window manager</em> maintains a sliding window of the most recent interactions, automatically removing older messages when limits are reached. The following example shows how to configure a sliding window manager that keeps the six most recent messages and activates when the message count exceeds 20:</p>
<pre>{
  "type": "SlidingWindowManager",
  "config": {
    "max_messages": <span class="pl-c1 rich-diff-level-one">6</span>,
    "activation": {
      "message_count_exceed": <span class="pl-c1 rich-diff-level-one">20</span>
    }
  }
}</pre>
<h4>Summarization manager</h4>
<p>The <em class="rich-diff-level-one">summarization manager</em> intelligently summarizes older interactions using large language models, preserving essential information while reducing token count. The following example configures summarization that preserves the 10 most recent messages, compresses older messages to 30% of their original size, and activates when the token count exceeds 200,000:</p>
<pre>{
  "type": "SummarizationManager",
  "config": {
    "summary_ratio": <span class="pl-c1 rich-diff-level-one">0.3</span>,
    "preserve_recent_messages": <span class="pl-c1 rich-diff-level-one">10</span>,
    "activation": {
      "tokens_exceed": <span class="pl-c1 rich-diff-level-one">200000</span>
    }
  }
}</pre>
<h4>Tools output truncate manager</h4>
<p>The <em class="rich-diff-level-one">tools output truncate manager</em> truncates tool outputs that exceed specified limits, preventing single large outputs from overwhelming the context. The following example limits tool outputs to 100,000 characters:</p>
<pre>{
  "type": "ToolsOutputTruncateManager",
  "config": {
    "max_output_length": <span class="pl-c1 rich-diff-level-one">100000</span>
  }
}</pre>
<h2>Smart activation rules</h2>
<p>Context managers use <em class="rich-diff-level-one">activation rules</em> to determine when optimization is needed. The <code class="rich-diff-level-one">tokens_exceed</code> rule activates when the estimated token count exceeds a threshold, while the <code class="rich-diff-level-one">message_count_exceed</code> rule activates when the message count exceeds a limit. You can combine multiple rules using <code class="rich-diff-level-one">AND</code> logic for precise control. This means your agents only perform expensive operations like summarization when actually needed.</p>
<h2>Real-world use cases</h2>
<p>Context management performs well in scenarios in which agents need to maintain long conversations while managing resource constraints.</p>
<h3>Customer service agent</h3>
<p>For a customer service agent that handles multiple short interactions, you can configure a sliding window manager to keep only the most recent messages while truncating large tool outputs. The following example creates a context management configuration that maintains the six most recent messages (activating after 15 messages) and limits tool outputs to 50,000 characters:</p>
<pre><span class="pl-ii rich-diff-level-one">POST /_plugins/_ml/context_management/customer-service-optimizer</span>
{
  "description": "Optimized context management for customer service interactions",
  "hooks": {
    "pre_llm": [
      {
        "type": "SlidingWindowManager",
        "config": {
          "max_messages": <span class="pl-c1 rich-diff-level-one">6</span>,
          "activation": {
            "message_count_exceed": <span class="pl-c1 rich-diff-level-one">15</span>
          }
        }
      }
    ],
    "post_tool": [
      {
        "type": "ToolsOutputTruncateManager",
        "config": {
          "max_output_length": <span class="pl-c1 rich-diff-level-one">50000</span>
        }
      }
    ]
  }
}</pre>
<h3>Research assistant with heavy tool usage</h3>
<p>For a research assistant that uses many tools and accumulates large amounts of context, you can combine summarization with output truncation. The following example creates a configuration that summarizes older messages (preserving the eight most recent messages), activates when tokens exceed 150,000, and limits tool outputs to 80,000 characters:</p>
<pre><span class="pl-ii rich-diff-level-one">POST /_plugins/_ml/context_management/research-assistant-optimizer</span>
{
  "description": "Context management for research agents with extensive tool interactions",
  "hooks": {
    "pre_llm": [
      {
        "type": "SummarizationManager",
        "config": {
          "summary_ratio": <span class="pl-c1 rich-diff-level-one">0.4</span>,
          "preserve_recent_messages": <span class="pl-c1 rich-diff-level-one">8</span>,
          "activation": {
            "tokens_exceed": <span class="pl-c1 rich-diff-level-one">150000</span>
          }
        }
      }
    ],
    "post_tool": [
      {
        "type": "ToolsOutputTruncateManager",
        "config": {
          "max_output_length": <span class="pl-c1 rich-diff-level-one">80000</span>
        }
      }
    ]
  }
}</pre>
<h2>Implementing context management</h2>
<p>To implement context management, first create a context management configuration with your desired managers and rules (as shown in the use cases above). Then register your agent with that configuration by referencing the configuration name in your agent registration. The following example registers a conversational agent with the customer service optimizer configuration:</p>
<pre><span class="pl-ii rich-diff-level-one">POST /_plugins/_ml/agents/_register</span>
{
  "name": "my-smart-agent",
  "type": "conversational",
  "llm": {
    "model_id": "your-llm-model-id"
  },
  "context_management_name": "customer-service-optimizer"
}</pre>
<p>Once registered, execute your agent and observe intelligent context optimization in action. You can even specify different context management templates for individual executions. The following example executes an agent using the research assistant optimizer configuration:</p>
<pre><span class="pl-ii rich-diff-level-one">POST /_plugins/_ml/agents/agent-id/_execute</span>
{
  "parameters": {
    "question": "How can I help you today?"
  },
  "context_management_name": "research-assistant-optimizer"
}</pre>
<p>After deployment, monitor your agent&#8217;s performance and adjust configurations based on observed behavior and resource usage patterns.</p>
<h2>Next steps</h2>
<p>Context management is available in OpenSearch 3.5. Review the <a class="rich-diff-level-one" href="https://opensearch.org/docs/latest/ml-commons-plugin/context-management/" rel="nofollow">context management documentation</a> and start experimenting with different configurations to find what works best for your use cases.</p>
<p>The hook-based architecture is designed for extensibility, providing a foundation for even more sophisticated context optimization strategies. You can build custom context managers for specialized use cases, add new execution hooks at different points in the agent lifecycle, or implement advanced activation rules.</p>
<p>The OpenSearch community welcomes contributions! Whether you have ideas for new context optimization strategies or want to extend the hook system, review our <a class="rich-diff-level-one" href="https://github.com/opensearch-project/ml-commons/blob/main/CONTRIBUTING.md">contribution guidelines</a> and join the conversation on <a class="rich-diff-level-one" href="https://github.com/opensearch-project/ml-commons">GitHub</a> or the <a class="rich-diff-level-one" href="https://forum.opensearch.org/" rel="nofollow">community forum</a>.</p>
<p>The post <a href="https://opensearch.org/blog/solving-context-overflow-how-opensearch-agents-stay-smart-in-long-conversations/">Solving context overflow: How OpenSearch agents stay smart in long conversations</a> appeared first on <a href="https://opensearch.org">OpenSearch</a>.</p>
