---
paper id: 2506.02153v2
title: Small Language Models are the Future of Agentic AI
authors: [Peter Belcak, Greg Heinrich, Shizhe Diao, Yonggan Fu, Xin Dong, Saurav Muralidharan, Yingyan Celine Lin, Pavlo Molchanov]
publication date: 2025-06-02T18:35
abstract: |
  Large language models (LLMs) are often praised for exhibiting near-human performance on a wide range of tasks and valued for their ability to hold a general conversation. The rise of agentic AI systems is, however, ushering in a mass of applications in which language models perform a small number of specialized tasks repetitively and with little variation.
    Here we lay out the position that small language models (SLMs) are sufficiently powerful, inherently more suitable, and necessarily more economical for many invocations in agentic systems, and are therefore the future of agentic AI. Our argumentation is grounded in the current level of capabilities exhibited by SLMs, the common architectures of agentic systems, and the economy of LM deployment. We further argue that in situations where general-purpose conversational abilities are essential, heterogeneous agentic systems (i.e., agents invoking multiple different models) are the natural choice. We discuss the potential barriers for the adoption of SLMs in agentic systems and outline a general LLM-to-SLM agent conversion algorithm.
    Our position, formulated as a value statement, highlights the significance of the operational and economic impact even a partial shift from LLMs to SLMs is to have on the AI agent industry. We aim to stimulate the discussion on the effective use of AI resources and hope to advance the efforts to lower the costs of AI of the present day. Calling for both contributions to and critique of our position, we commit to publishing all such correspondence at https://research.nvidia.com/labs/lpr/slm-agents.
comments: ""
pdf: "[[Master Thesis Papers/Small Language Models are the Future of Agentic AI (2506.02153v2).pdf]]"
url: https://arxiv.org/abs/2506.02153v2
tags: []
---
## Key Findings
(V1) SLMs are principally sufficiently powerful to handle the language modeling tasks in agentic applications; (V2) SLMs are inherently more operationally suitable for use in agentic systems than Large Language Models (LLMs); and (V3) SLMs are necessarily more economical for the vast majority of LM uses in agentic systems due to their smaller size. Furthermore, analyses of popular agents suggest a significant portion of LLM queries (e.g., 40% to 70% in case studies) could be reliably handled by specialized SLMs

## Limitations
1. Large amounts of upfront investment in centralized LLM inference infrastructure, creating industry inertia.
2. The continued use of generalist benchmarks in SLM design and evaluation, rather than focusing on metrics measuring agentic utility. 
3. Lack of popular awareness and marketing intensity compared to LLMs. The authors also acknowledge alternative views, such as the persistent belief that LLM generalists will always have the advantage of broader language understanding (AV1) and the possibility that the economy of scale for centralized LLMs might dwarf the per-token cost benefit of SLMs (AV2).

## **Paper Summary**
---

The paper, "Small Language Models are the Future of Agentic AI," lays out a strong position that **SLMs are inherently more suitable, sufficiently powerful, and necessarily more economical** for the majority of invocations within agentic AI systems compared to their general-purpose LLM counterparts. The argument stems from the observation that while LLMs offer impressive generality and conversational fluency, most subtasks performed by deployed AI agents are repetitive, narrowly scoped, and non-conversational, demanding models that are efficient, predictable, and inexpensive.

The authors support their position by demonstrating that **SLMs now supply sufficient reasoning power** for agentic work. Recent advances show that well-designed SLMs, such as the Microsoft Phi series (2.7bn parameters) or DeepMind RETRO (7.5bn parameters), can achieve capabilities in commonsense reasoning, code generation, and instruction following comparable to or even exceeding LLMs up to 70bn parameters or more, sometimes running up to 15 times faster. This capability, combined with light-weight fine-tuning or inference augmentation (like tool augmentation), shows that **capability, not parameter count, is the binding constraint**.

Economically, SLMs offer immense advantages (V3): serving a 7bn SLM can be 10–30 times cheaper (in latency, energy consumption, and FLOPs) than serving a 70–175bn LLM. SLMs also promote **fine-tuning agility**, allowing specialization to be performed overnight using only a few GPU-hours. Operationally (V2), SLMs enable greater flexibility, democratization of agent development, and close behavioral alignment necessary for precise interactions with code (e.g., strict JSON/XML formatting requirements). The architecture of agentic systems naturally allows for heterogeneity, where SLMs can handle subordinate or specialized tasks, reserving LLMs for selective, sparing use, thus creating more cost-effective, modular, and sustainable systems.

To facilitate the transition, the paper proposes a six-step **LLM-to-SLM Agent Conversion Algorithm**. This process involves securing usage data collection (S1), curating and filtering the data (S2), clustering tasks to identify specialization candidates (S3), selecting suitable SLMs (S4), fine-tuning the specialized SLMs (S5), and establishing a continuous improvement loop (S6). The effectiveness of this approach is illustrated through case studies of open-source agents (MetaGPT, Open Operator, and Cradle), which suggest that between 40% and 70% of their LLM queries could be replaced by specialized SLMs.

Ultimately, the paper aims to stimulate discussion on the effective use of AI resources, arguing that shifting toward SLM-first architectures is necessary for **promoting responsible and sustainable AI deployment** by lowering infrastructure costs and environmental impact
