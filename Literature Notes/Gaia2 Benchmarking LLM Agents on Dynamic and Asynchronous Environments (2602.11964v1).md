---
paper id: 2602.11964v1
title: "Gaia2: Benchmarking LLM Agents on Dynamic and Asynchronous Environments"
authors:
  - Romain Froger
  - Pierre Andrews
  - Matteo Bettini
  - Amar Budhiraja
  - Ricardo Silveira Cabral
  - Virginie Do
  - Emilien Garreau
  - Jean-Baptiste Gaya
  - Hugo Laurençon
  - Maxime Lecanu
  - Kunal Malkan
  - Dheeraj Mekala
  - Pierre Ménard
  - Gerard Moreno-Torres Bertran
  - Ulyana Piterbarg
  - Mikhail Plekhanov
  - Mathieu Rita
  - Andrey Rusakov
  - Vladislav Vorotilov
  - Mengjue Wang
  - Ian Yu
  - Amine Benhalloum
  - Grégoire Mialon
  - Thomas Scialom
publication date: 2026-02-12T13:58
abstract: 'We introduce Gaia2, a benchmark for evaluating large language model agents in realistic, asynchronous environments. Unlike prior static or synchronous evaluations, Gaia2 introduces scenarios where environments evolve independently of agent actions, requiring agents to operate under temporal constraints, adapt to noisy and dynamic events, resolve ambiguity, and collaborate with other agents. Each scenario is paired with a write-action verifier, enabling fine-grained, action-level evaluation and making Gaia2 directly usable for reinforcement learning from verifiable rewards. Our evaluation of state-of-the-art proprietary and open-source models shows that no model dominates across capabilities: GPT-5 (high) reaches the strongest overall score of 42% pass@1 but fails on time-sensitive tasks, Claude-4 Sonnet trades accuracy and speed for cost, Kimi-K2 leads among open-source models with 21% pass@1. These results highlight fundamental trade-offs between reasoning, efficiency, robustness, and expose challenges in closing the "sim2real" gap. Gaia2 is built on a consumer environment with the open-source Agents Research Environments platform and designed to be easy to extend. By releasing Gaia2 alongside the foundational ARE framework, we aim to provide the community with a flexible infrastructure for developing, benchmarking, and training the next generation of practical agent systems.'
comments: Accepted as Oral at ICLR 2026
pdf: "[[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf]]"
url: https://arxiv.org/abs/2602.11964v1
tags: []
---
> [!PDF|yellow] [[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf#page=2&selection=29,0,36,1&color=yellow|Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1), p.2]]
> > Gaia2 consists of 1,120 human-annotated scenarios set in a smartphone-like environment with realistic apps (email, messaging, calendar, contacts, etc.), similar to AppWorld and ToolSandbox (Trivedi et al., 2024; Lu et al., 2024). Each scenario requires capabilities beyond search and execution, including adaptability to new events, robustness to noise, resolution of ambiguity, temporal awareness, and collaboration with other agents.
> 
> **NOTE: is it then relevant/feasible within the thesis scope?**

> [!PDF|yellow] [[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf#page=4&selection=29,0,34,95&color=yellow|Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1), p.4]]
> > Asynchronicity and time Because environments run asynchronously, model generations directly consume simulated time: if an agent takes longer to respond, the environment clock still advances, and external events may happen during its reasoning process. This design unlocks evaluations of temporal awareness and responsiveness, which are impossible to capture in synchronous settings.
> 
> **Tricky with our setup that has locks over the same LLM**

> [!PDF|yellow] [[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf#page=4&selection=53,0,55,1&color=yellow|Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1), p.4]]
> > Universes contain between 400K and 800K tokens of structured and unstructured content (excluding filesystem contents), making them suited for long-context and long-horizon tasks. 
> 
> **>> context window for SLMs**

> [!PDF|red] [[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf#page=4&selection=107,0,118,76&color=red|Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1), p.4]]
> > Building on the abstractions of ARE, we introduce Gaia2, consisting of 800 unique verifiable scenarios, carefully annotated by humans across 10 distinct universes in the Mobile environment, with 101 tools each. 
> 
> !!!

> [!PDF|yellow] [[Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1).pdf#page=5&selection=116,0,129,3&color=yellow|Gaia2 Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1), p.5]]
> > Gaia2 evaluates agents across 1,120 scenarios. To provide a clear taxonomy, we distinguish between Core Capabilities (Execution, Search, Ambiguity, Adaptability, Time) and Augmentations (Noise, A2A). 

