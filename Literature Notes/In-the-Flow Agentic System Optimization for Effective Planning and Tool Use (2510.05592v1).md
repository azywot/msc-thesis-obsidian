---
paper id: 2510.05592v1
title: "In-the-Flow Agentic System Optimization for Effective Planning and Tool Use"
authors: [Zhuofeng Li, Haoxiang Zhang, Seungju Han, Sheng Liu, Jianwen Xie, Yu Zhang, Yejin Choi, James Zou, Pan Lu]
publication date: 2025-10-07T05:32
abstract: "Outcome-driven reinforcement learning has advanced reasoning in large language models (LLMs), but prevailing tool-augmented approaches train a single, monolithic policy that interleaves thoughts and tool calls under full context; this scales poorly with long horizons and diverse tools and generalizes weakly to new scenarios. Agentic systems offer a promising alternative by decomposing work across specialized modules, yet most remain training-free or rely on offline training decoupled from the live dynamics of multi-turn interaction. We introduce AgentFlow, a trainable, in-the-flow agentic framework that coordinates four modules (planner, executor, verifier, generator) through an evolving memory and directly optimizes its planner inside the multi-turn loop. To train on-policy in live environments, we propose Flow-based Group Refined Policy Optimization (Flow-GRPO), which tackles long-horizon, sparse-reward credit assignment by converting multi-turn optimization into a sequence of tractable single-turn policy updates. It broadcasts a single, verifiable trajectory-level outcome to every turn to align local planner decisions with global success and stabilizes learning with group-normalized advantages. Across ten benchmarks, AgentFlow with a 7B-scale backbone outperforms top-performing baselines with average accuracy gains of 14.9% on search, 14.0% on agentic, 14.5% on mathematical, and 4.1% on scientific tasks, even surpassing larger proprietary models like GPT-4o. Further analyses confirm the benefits of in-the-flow optimization, showing improved planning, enhanced tool-calling reliability, and positive scaling with model size and reasoning turns."
comments: "45 pages, 12 figures. Project website: https://agentflow.stanford.edu/"
pdf: "[[Master Thesis Papers/In-the-Flow Agentic System Optimization for Effective Planning and Tool Use (2510.05592v1).pdf]]"
url: https://arxiv.org/abs/2510.05592v1
tags: []
---
## Key Findings
Superior performance across ten benchmarks, substantially outperforming specialized baselines and proprietary models like GPT-4o. Achieved average accuracy gains of 14.9% on search, 14.0% on agentic, 14.5% on mathematical, and 4.1% on scientific tasks over top baselines. In-the-flow optimization is crucial and prevents the catastrophic collapse observed with offline supervised fine-tuning (SFT). Flow-GRPO leads to improved planning, enhanced tool-calling reliability (error rate reduction up to 28.4% on GAIA), and positive scaling with model size and allowed reasoning turns.

## Methodology
AGENTFLOW is a trainable, in-the-flow agentic framework coordinating four modules (planner, executor, verifier, generator) through an evolving memory. The framework directly optimizes the Action Planner policy on-policy inside the multi-turn loop. The optimization uses Flow-based Group Refined Policy Optimization (Flow-GRPO). Flow-GRPO tackles long-horizon, sparse-reward credit assignment by converting multi-turn RL into a sequence of tractable single-turn policy updates through broadcasting a single, verifiable trajectory-level outcome reward to every turn. All modules were instantiated using the Qwen2.5-7B-Instruct model as the backbone, except the Action Planner, which was trained

## **Paper Summary**

---

![image.png](attachment:1cd5a854-7f03-491b-8b47-7bfd897e20ef:image.png)

![image.png](attachment:9dd79ac0-acb4-49d1-94ec-49447089ba25:image.png)

The sources introduce **AGENTFLOW**, a trainable, in-the-flow agentic framework designed to address the challenges associated with complex, long-horizon reasoning tasks that require external tools. Existing tool-augmented approaches typically train a single, monolithic policy which scales poorly, leads to training instability, and results in brittle generalization. While training-free agentic systems decompose tasks using specialized modules, they struggle to robustly coordinate modules or adapt to evolving tool outputs because they are decoupled from the live dynamics of interaction.

AGENTFLOW resolves these issues by coordinating **four specialized modules: the Action Planner (_**P**_), Tool Executor (_**E**_), Execution Verifier (_**V**_), and Solution Generator (_**G**_)**, through a **shared evolving memory (_**M**_)**. This system operates iteratively in the flow, cycling through planning, execution, and verification. A critical distinction is that AGENTFLOW **directly optimizes its Action Planner (the trainable policy** _πθ_**) on-policy**, inside the live multi-turn loop, allowing it to dynamically adapt to tool call results and memory updates. The evolving memory maintains a deterministic, structured record of the reasoning process, ensuring transparency and bounding context growth.

To enable stable on-policy training under long-horizon, sparse-reward settings, the paper proposes **Flow-based Group Refined Policy Optimization (Flow-GRPO)**. Flow-GRPO addresses the multi-turn credit assignment problem by assigning a **single, verifiable final-outcome reward** to the entire trajectory and **broadcasting it to every turn**. This action effectively converts the multi-turn reinforcement learning challenge into a sequence of tractable single-turn policy updates, where each update is conditioned on the full historical context and aligned with global success. Training is further stabilized using group-normalized advantages and KL regularization against a reference policy. The reward signal is provided by an LLM-as-judge, specifically GPT-4o, to determine the correctness of the final solution.

Comprehensive experiments were conducted across ten diverse benchmarks in four reasoning domains: search-intensive, agentic, mathematical, and scientific reasoning. AGENTFLOW, using a 7B-scale backbone (Qwen2.5-7B-Instruct) for all modules, **substantially outperformed top-performing baselines**. Over specialized models, AGENTFLOW achieved average accuracy gains of 14.9% on search tasks, 14.0% on agentic tasks, 14.5% on mathematical tasks, and 4.1% on scientific tasks. The 7B-backbone AGENTFLOW system notably **surpassed the performance of the much larger proprietary GPT-4o model** across all evaluated domains.

In-depth analysis demonstrated the tangible benefits of Flow-GRPO: it significantly **enhanced tool-calling efficacy** by reducing the tool-calling error rate by up to 28.4% on GAIA. The trained planner learned to select task-appropriate tools dynamically, such as increasing Google Search usage for broad factual tasks (like 2Wiki) while shifting towards specialized Web Search or Wikipedia Search for domain-specific tasks (like MedQA). Crucially, the in-the-flow optimization proved essential, as ablations showed that conventional offline **Supervised Fine-Tuning (SFT) resulted in a catastrophic performance collapse (an average 19.0% drop compared to the frozen baseline), underscoring the necessity of optimizing the planner within the live system dynamics. The framework also showed positive scaling, with consistent performance improvements when increasing the backbone size (3B to 7B) and extending the maximum allowed reasoning turns (up to _Tmax_=10)**

### NOTES

---

The sources explicitly confirm that the **Action Planner** was the _only_ component within the AGENTFLOW framework that was trained and optimized, using the Qwen2.5-7B-Instruct model as its backbone.

However, the sources **do not specify** whether the training involved **full fine-tuning** (where all parameters of the Action Planner's Qwen2.5-7B-Instruct backbone were unfrozen and updated) or whether a **parameter-efficient fine-tuning (PEFT) method** (such as LoRA, which only trains selected layers or injected parameters) was used.

| Feature       | Monolithic TIR Models                                                                                                 | AGENTFLOW (Agentic System)                                                                                          |
| ------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Structure** | A single policy that interleaves reasoning (<think>) and tool calls (<tool call>) within one full-context trajectory. | **Multiple specialized modules** (Planner, Executor, Verifier, Generator) that collaborate via shared memory.       |
| **Scaling**   | Scales poorly as horizons lengthen and tool diversity grows.                                                          | Decomposes tasks across specialized components to tackle long horizons and diverse tools.                           |
| **Training**  | Trains a single policy, often leading to instability and brittle generalization.                                      | Optimizes only the **Action Planner** on-policy _inside the multi-turn loop_, while other modules are often frozen. |
