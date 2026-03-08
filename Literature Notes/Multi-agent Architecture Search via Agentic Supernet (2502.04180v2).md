---
paper id: 2502.04180v2
title: "Multi-agent Architecture Search via Agentic Supernet"
authors: [Guibin Zhang, Luyang Niu, Junfeng Fang, Kun Wang, Lei Bai, Xiang Wang]
publication date: 2025-02-06T16:12
abstract: "Large Language Model (LLM)-empowered multi-agent systems extend the cognitive boundaries of individual agents through disciplined collaboration and interaction, while constructing these systems often requires labor-intensive manual designs. Despite the availability of methods to automate the design of agentic workflows, they typically seek to identify a static, complex, one-size-fits-all system, which, however, fails to dynamically allocate inference resources based on the difficulty and domain of each query. To address this challenge, we shift away from the pursuit of a monolithic agentic system, instead optimizing the \\textbf{agentic supernet}, a probabilistic and continuous distribution of agentic architectures. We introduce MaAS, an automated framework that samples query-dependent agentic systems from the supernet, delivering high-quality solutions and tailored resource allocation (\\textit{e.g.}, LLM calls, tool calls, token cost). Comprehensive evaluation across six benchmarks demonstrates that MaAS \\textbf{(I)} requires only $6\\sim45\\%$ of the inference costs of existing handcrafted or automated multi-agent systems, \\textbf{(II)} surpasses them by $0.54\\%\\sim11.82\\%$, and \\textbf{(III)} enjoys superior cross-dataset and cross-LLM-backbone transferability."
comments: ""
pdf: "[[Master Thesis Papers/Multi-agent Architecture Search via Agentic Supernet (2502.04180v2).pdf]]"
url: https://arxiv.org/abs/2502.04180v2
tags: []
---
## Key Findings:
MaAS requires only 6% ∼ 45% of the inference costs of existing systems and surpasses them by 0.54% ∼ 16.89% in performance. MaAS achieved an average best score of 83.59% across mathematical reasoning and code generation benchmarks. The framework also demonstrates superior cross-dataset and cross-LLM-backbone transferability

## Limitations:
1. Performance vs. Cost Trade-off (λ): MaAS operates under cost-constrained optimization, meaning that increasing the cost penalty coefficient (λ) to favor cost-efficient solutions results in some performance degradation.2. Architecture Depth Constraint (L): Increasing the number of cascaded layers (L) beyond L=4 yields only marginal performance gains while incurring higher per-query inference costs.3. Dependency on Textual Gradient: The system's performance is heavily reliant on the textual gradient (∇OL) for operator self-evolution; removing this component causes the largest performance drop.

# Paper Summary

The paper introduces **Multi-agent Architecture Search (MaAS)**, an automated framework designed to address the limitations of existing multi-agent systems that rely on static, manually configured, or monolithic architectures

![image.png](attachment:6e3feb82-8cc0-4d86-b0c5-e4798a6a884f:image.png)

**Paradigm Shift and Agentic Supernet:** MaAS reformulates the design problem by shifting from optimizing a single optimal multi-agent system to optimizing the **agentic supernet** (A). The agentic supernet is defined as a probabilistic, continuous distribution of architectures, consisting of a set of **agentic operators** (O) and their parameterized probability distributions (_π_) across cascaded layers (_L_). Agentic operators are composite LLM-agent invocation processes that may involve multiple LLM calls, prompts, and tool usages, such as Chain-of-Thought (CoT), ReAct, Debate, and Self-Refine.

**Query-Dependent Sampling:** During inference, MaAS samples a query-dependent agentic system (_G_) from the supernet. A **controller network (_**Qϕ**_)** conditions the sampling process on the input query (_q_). The controller utilizes a **Mixture-of-Expert (MoE)-style network** where activation scores determine which operators are selected per layer, ensuring that resource allocation is dynamic and dependent on task complexity. To maximize resource efficiency, MaAS incorporates an **early-exit operator (_**Oexit**_)**, which interrupts the architecture sampling process when a satisfactory solution is found simply (e.g., for easy elementary-level arithmetic problems that only require a single zero-shot I/O).

**Cost-Constrained Optimization:** MaAS optimizes the supernet by jointly updating the distribution (_π_) and the operators (O) to maximize utility (performance) _U_(⋅) while minimizing cost _C_(⋅) (token cost).

1. **Distribution Optimization (**∇_πL_**):** Since the utility calculation often involves non-differentiable API calls, MaAS employs an **empirical Bayes Monte Carlo procedure** to estimate the gradient. This process uses cost-aware importance weights to update the distribution _π_ to favor architectures that achieve high-quality solutions with minimal token cost.
    
2. **Operator Optimization (**∇O_L_**):** Because operators contain black-box tools and natural language prompts, numerical gradient updates are infeasible. Instead, MaAS uses **textual gradient** (agent-generated gradient analyses in textual format) to approximate backpropagation and update operator components, such as prompts, model temperature, or the internal node structure of the operators themselves.
    

This automated, resource-aware approach allows MaAS to achieve higher performance while requiring significantly lower inference costs compared to state-of-the-art handcrafted or automated multi-agent systems

## NOTES:

---

The **Controller network** (_Qϕ_) in the MaAS framework is a specialized component responsible for determining the structure of the multi-agent system dynamically based on the input query - it is implemented as a **Mixture-of-Expert (MoE)-style network**

### Controller flow:

The flow in the MaAS controller network (_Qϕ_) sequentially determines the agents (operators) selected for the query-dependent multi-agent system (_G_):

1. **Initialize Layer:** Start the sequential sampling procedure at layer ℓ=1.
    
2. **Calculate Activation Scores:** Compute activation scores (_S_) for all feasible agentic operators (O) using a Feed-Forward Network (FFN). This calculation is conditioned on the input query (_q_) and the embeddings (_v_(⋅)) of all operators selected in preceding layers.
    
3. **Select Operators (**_V_ℓ**):** Sort the activation scores (_S_↓) and sequentially activate operators until their cumulative score exceeds a predefined **threshold (**thres**)**, forming the set of selected operators _V_ℓ for the current layer.
    
4. **Check Early Exit:** Check if the **early-exit operator (_**Oexit**_)** is included in _V_ℓ. If it is, **interrupt** the sampling process immediately.
    
5. **Form Architecture and Iterate:** If the maximum layer depth (_L_) has not been reached and _Oexit_ was not selected, define the current architecture _G_ as ⟨_V_1,…,_V_ℓ⟩ and proceed to the next layer