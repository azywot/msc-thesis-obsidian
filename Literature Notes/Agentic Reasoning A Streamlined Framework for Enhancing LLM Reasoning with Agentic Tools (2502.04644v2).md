---
paper id: 2502.04644v2
title: "Agentic Reasoning: A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools"
authors: [Junde Wu, Jiayuan Zhu, Yuyuan Liu, Min Xu, Yueming Jin]
publication date: 2025-02-07T04:08
abstract: "We introduce Agentic Reasoning, a framework that enhances large language model (LLM) reasoning by integrating external tool-using agents. Agentic Reasoning dynamically leverages web search, code execution, and structured memory to address complex problems requiring deep research. A key innovation in our framework is the Mind-Map agent, which constructs a structured knowledge graph to store reasoning context and track logical relationships, ensuring coherence in long reasoning chains with extensive tool usage. Additionally, we conduct a comprehensive exploration of the Web-Search agent, leading to a highly effective search mechanism that surpasses all prior approaches. When deployed on DeepSeek-R1, our method achieves a new state-of-the-art (SOTA) among public models and delivers performance comparable to OpenAI Deep Research, the leading proprietary model in this domain. Extensive ablation studies validate the optimal selection of agentic tools and confirm the effectiveness of our Mind-Map and Web-Search agents in enhancing LLM reasoning. The code is at: https://github.com/theworldofagents/Agentic-Reasoning"
comments: ACL 2025
pdf: "[[Master Thesis Papers/Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools (2502.04644v2).pdf]]"
url: https://arxiv.org/abs/2502.04644v2
tags: []
---
## Key Findings
Agentic Reasoning achieves new state-of-the-art (SOTA) results among public models on **expert-level problems and deep research tasks**, delivering performance comparable to proprietary models like OpenAI Deep Research. The framework boosts overall performance on the GPQA dataset by nearly 10% compared to the base DeepSeek-R1 model. The combination of Web-Search, Code, and Mind-Map agents provides optimal and synergistic performance improvement

## Limitations
The system faces challenges including significant computational overhead and increased inference latency due to the sequential invocation of multiple external agents. Its reliance on external knowledge sources, particularly web search, makes it susceptible to misinformation or biased content due to the lack of built-in verification mechanisms. Furthermore, the system is vulnerable to hallucinations, a risk associated with its high dependence on LLMs for the overall decision-making process, necessitating better interpretability and trustworthiness.

## **Paper Summary**
---

![image.png](attachment:4b365a31-e63e-466b-9999-114da55024af:image.png)

The paper introduces **Agentic Reasoning**, a streamlined framework designed to enhance LLM reasoning, particularly for complex, knowledge-intensive, and less structured problems that require deep research, factual verification, and understanding complex logical relationships. The core idea is to allow a reasoning LLM to dynamically delegate specific tasks to auxiliary, specialized LLM-based agents, mimicking how humans use external tools like the internet and mind maps for complex analysis.

The framework identifies and integrates three universally effective agents: the **Web-Search agent**, the **Code agent**, and the **Mind-Map agent**. The reasoning LLM (DeepSeek-R1 was the primary model used) determines when to call these tools, embedding specialized tokens and queries into its reasoning sequence.

A key innovation is the **Mind-Map agent**, which functions as a structured memory by converting raw reasoning chains into a knowledge graph. This allows the framework to store reasoning context, track logical relationships, summarize clusters of information, and maintain coherence over long reasoning chains and massive tool calls. The Mind-Map proved crucial for complex logic-based questions and strategic reasoning, such as in the game Werewolf, where it significantly improved the model’s win rate.

The **Web-Search agent** utilizes a highly effective search mechanism that includes **query breakdown**, re-ranking of results, and RAG (Retrieval-Augmented Generation), surpassing all prior RAG and search approaches. The **Code agent** handles quantitative computations by generating and executing code using a specialized coding LLM (Claude-3.5-Sonnet), allowing the main reasoning model to remain focused on its core reasoning process.

When evaluated on expert-level benchmarks, Agentic Reasoning achieved a **new state-of-the-art (SOTA)** among public models. On Humanity's Last Exam, it achieved 23.8% accuracy with DeepSeek-R1, marking a 14.4% improvement over the base model and narrowing the gap to the proprietary OpenAI Deep Research to just 2.8%. On the GPQA dataset (a PhD-level science QA benchmark), the framework boosted overall performance by nearly 10% on DeepSeek-R1, reaching 81.2% overall accuracy and surpassing even the best proprietary model, o3-mini-high. Furthermore, in human evaluations of articles generated for deep research tasks, Agentic Reasoning outperformed all search-based methods and proprietary models like Gemini Deep Research across criteria such as interest level, organization, relevance, and coverage. Ablation studies confirmed that the combination of all three agents (Web Search, Coding, and Mind-Map) yields the best synergistic performance, and that increasing the number of tools beyond these three often degrades performance.

The Agentic Reasoning framework operates somewhat like a high-performing student tackling a complex research paper: the reasoning LLM is the student's mind, but it uses external aids—the Web-Search agent acts as specialized access to a library, the Code agent is a pocket calculator for quick computation, and the Mind-Map agent functions as a detailed, structured outline or note card system to prevent the student from losing track of intricate relationships during a long process.