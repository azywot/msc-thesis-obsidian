-------

## Table of Contents

- [Multi-Agent System (MAS) and SLMs](#multi-agent-system-mas-and-slms)
  - [MAS Literature](#mas-literature)
  - [Small Agents Literature](#small-agents-literature)
- [Datasets](#datasets)
- [Fine-tuning](#fine-tuning)
- [Thesis relevance](#thesis-relevance)

---------
# Multi-Agent System (MAS) and SLMs
## MAS Literature

#### [Small Language Models are the Future of Agentic AI (2506.02153v2)](Master%20Thesis%20Papers/Small%20Language%20Models%20are%20the%20Future%20of%20Agentic%20AI%20(2506.02153v2).pdf)
Belcak et al. argue that the current reliance on generalist LLMs in agentic architectures represents an economically inefficient misallocation of computational resources.
- They advocate for heterogeneous agentic systems where complex goals are decomposed into modular sub-tasks.
- The authors observe that agentic applications typically act as heavily instructed gateways that restrict a language model to a very small subset of its overall capabilities.
- Because tasks are broken down into narrow, scoped operations, the broad "semantic hub" and generalized reasoning capabilities of massive LLMs become unnecessary at the execution level.
- By combining the precision and efficiency of SLMs with the selective use of LLMs for general reasoning, developers can build modular, "Lego-like" systems that are easier to debug, adapt, and scale.
> [!PDF|yellow] [[Small Language Models are the Future of Agentic AI (2506.02153v2).pdf#page=5&selection=72,0,76,86&color=yellow|Small Language Models are the Future of Agentic AI (2506.02153v2), p.5]]
> > The above-mentioned “Lego-like” composition of agentic intelligence—scaling out by adding small, specialized experts instead of scaling up monolithic models—yields systems that are cheaper, faster to debug, easier to deploy, and better aligned with the operational diversity of real-world agents. When combined with tool calling, caching, and fine-grained routing, SLM-first architectures appear to offer the best path forward for cost-effective, modular, and sustainable agentic AI
> 


#### [Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools](Master%20Thesis%20Papers/Agentic%20Reasoning%20A%20Streamlined%20Framework%20for%20Enhancing%20LLM%20Reasoning%20with%20Agentic%20Tools%20(2502.04644v2).pdf)
- Wu et al. propose *Agentic Reasoning*, a framework designed to enhance large language model reasoning by integrating external, tool-using agents.
- This approach decouples high-level reasoning from execution by allowing the main reasoning LLM to delegate specific sub-tasks to specialized auxiliary agents, which prevents the main model from being disrupted by tasks like writing and executing code.
- The authors experimentally identify three universally effective agentic tools: a **Web-Search agent, a Coding agent, and a Mind-Map memory agent.**
- A key contribution relevant to minimal orchestration is their finding on **tool quantity versus quality; ablation studies revealed that adding massive toolboxes (such as LangChain's 109 tools) actually degraded overall performance due to an increased risk of inappropriate tool selection.**
- The framework introduces the Mind-Map agent, which dynamically constructs a structured knowledge graph to store reasoning context, track logical relationships, and maintain coherence over long, multi-step reasoning chains.
- Furthermore, the authors demonstrate that wrapping tools in an "agentic" layer (where the tool is managed by an LLM) significantly reduces errors compared to traditional direct API calling, as the agent can self-monitor, express uncertainty, and prevent cascading failures.

> [!PDF|] [[Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools (2502.04644v2).pdf#page=15&selection=76,0,96,25|Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools (2502.04644v2), p.15]]
> > Using agentic tool calls rather than direct API calls offers several advantages: 1. Overcoming single-model token limitations: By structuring the workflow agentically, the system can break free from the token generation limits of a single LLM. This enables it to produce longer, higher-quality reasoning chains than would be possible within the token budget of a single model call. 2. Managing uncertainty and reducing error propagation: Agents can self-monitor and assign varying levels of confidence to their outputs. As noted earlier, this mechanism helps the reasoning model treat low-confidence outputs as tentative, thereb
> 

#### [Multi-agent Architecture Search via Agentic Supernet](Master%20Thesis%20Papers/Multi-agent%20Architecture%20Search%20via%20Agentic%20Supernet%20(2502.04180v2).pdf) 
- A framework that moves away from designing monolithic, static agentic systems by optimizing an **agentic supernet** - a probabilistic and continuous distribution of multi-agent architectures. 
- The authors argue that contemporary automated methods usually seek a complex, one-size-fits-all system, which fails to dynamically allocate inference resources based on the specific difficulty and domain of each query. To solve this, MaAS samples query-dependent architectures from the supernet, tailoring the system's resource allocation, including LLM calls and tool usage, to the task at hand.
- A critical component of their architecture is the "early-exit operator," which allows the system to halt multi-agent sampling early for simple queries, preventing unnecessary redundancy and resource expenditure.
- **The paper provides a strong counterpoint to static orchestration, showing that different domains require fundamentally different agentic topologies to succeed efficiently** 
> [!PDF|] [[Multi-agent Architecture Search via Agentic Supernet (2502.04180v2).pdf#page=2&selection=148,0,155,61|Multi-agent Architecture Search via Agentic Supernet (2502.04180v2), p.2]]
> > Figure 1. (Left) The building blocks of MaAS; (Right) When confronting different queries, the agentic supernet adaptively samples tailored multi-agent architecture in a query-dependent manner
> 




## Small Agents Literature

#### [Small Language Models are the Future of Agentic AI (2506.02153v2)](Master%20Thesis%20Papers/Small%20Language%20Models%20are%20the%20Future%20of%20Agentic%20AI%20(2506.02153v2).pdf)
This position paper formally contends that SLMs are sufficiently powerful, inherently more operationally suitable, and necessarily more economical for the vast majority of agentic invocations.
- The authors argue that the majority of subtasks in deployed systems are repetitive, scoped, and non-conversational, which perfectly suits the predictability of SLMs.
- Serving a 7B parameter SLM is estimated to be 10 to 30 times cheaper in terms of latency, energy consumption, and FLOPs compared to a 70B-175B parameter LLM.
- **SLMs also enforce closer behavioral alignment; they are less prone to hallucinatory format deviations when generating tool calls or interacting directly with code schemas .**
- In three case studies estimating LLM-to-SLM replacement in popular open-source agents (MetaGPT, Open Operator, Cradle), the authors estimate that 40% to 70% of LLM queries could be reliably replaced by appropriately specialized SLMs.



#### [Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools](Master%20Thesis%20Papers/Agentic%20Reasoning%20A%20Streamlined%20Framework%20for%20Enhancing%20LLM%20Reasoning%20with%20Agentic%20Tools%20(2502.04644v2).pdf)
While the primary experiments in this study utilize frontier models like DeepSeek-R1 and DeepSeek-V3, the architectural design strongly supports the principles of Small Language Model (SLM) ensembles. The authors highlight the advantage of **Task-specific model modularity**, which allows different language models to be assigned to different tasks based on their strengths. Specifically, they note that an agentic setup allows for the routing of simpler subtasks—such as summarizing web search results—to lightweight, non-reasoning models. This modularity optimizes resource usage and preserves efficiency by matching the best, potentially smaller, model to each specific subtask rather than relying on a monolithic model for every step.

#### [Multi-agent Architecture Search via Agentic Supernet](Master%20Thesis%20Papers/Multi-agent%20Architecture%20Search%20via%20Agentic%20Supernet%20(2502.04180v2).pdf) 
- While MaAS evaluates models of varying sizes, its core philosophy aligns with the goals of Small Language Model ensembles: **maximizing performance while strictly minimizing inference costs and token consumption.**
- The authors demonstrate that by dynamically sampling customized systems, MaAS requires only 6% to 45% of the inference costs compared to existing handcrafted or automated multi-agent systems.
- By proving that complex, token-heavy systems are largely unnecessary for simpler tasks (which can be resolved with single zero-shot I/O), MaAS reinforces the viability of utilizing smaller, specialized configurations to handle varying workloads efficiently




-----
# Datasets 

#### [Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools](Master%20Thesis%20Papers/Agentic%20Reasoning%20A%20Streamlined%20Framework%20for%20Enhancing%20LLM%20Reasoning%20with%20Agentic%20Tools%20(2502.04644v2).pdf)
- The authors utilize the **GAIA benchmark** to evaluate their system's ability to handle reasoning, web browsing, and tool-use proficiency. Their results on GAIA validate the necessity of multi-agent collaboration for complex tasks; they note that GAIA requires a combination of advanced reasoning and tool-use that benefits heavily from their agentic framework, surpassing prior search-in-reasoning approaches.
- The paper also evaluates expert-level problem-solving using datasets like **GPQA and Humanity's Last Exam,** demonstrating that well-orchestrated agentic systems can close the gap with proprietary, closed-source models on highly difficult, multi-step benchmarks.

#### [Multi-agent Architecture Search via Agentic Supernet](Master%20Thesis%20Papers/Multi-agent%20Architecture%20Search%20via%20Agentic%20Supernet%20(2502.04180v2).pdf) 
- MaAS conducts comprehensive evaluations across several benchmarks, **featuring GAIA for diverse tool usage, as well as HumanEval and MBPP for code generation, and GSM8K and MATH for mathematical reasoning.**
> [!PDF|] [[Multi-agent Architecture Search via Agentic Supernet (2502.04180v2).pdf#page=5&selection=602,0,618,29|Multi-agent Architecture Search via Agentic Supernet (2502.04180v2), p.5]]
> > Tasks and Benchmarks. We evaluate MaAS on six public benchmarks covering three domains: (1) math reasoning, GSM8K (Cobbe et al., 2021), MATH (Hendrycks et al., 2021), and MultiArith (Roy & Roth, 2016); (2) code generation, HumanEval (Chen et al., 2021) and MBPP (Austin et al., 2021)); and (3) tool use, GAIA (Mialon et al., 2023).
> 

The authors specifically note that in the GAIA benchmark, no single static system is optimal for both file reading and web searching tasks simultaneously.
> [!PDF|note] [[Multi-agent Architecture Search via Agentic Supernet (2502.04180v2).pdf#page=2&selection=173,33,183,59&color=note|Multi-agent Architecture Search via Agentic Supernet (2502.04180v2), p.2]]
> > there is no single system that is optimal for both file reading and web searching tasks, leaving practitioners with no alternative but to split the benchmark and optimize separately (Zhuge et al., 2024).

By adaptively sampling customized agentic systems based on the specific domain of the GAIA task, MaAS achieved substantial improvements over baselines, securing an 18.38% improvement on Level 1 tasks and a 17.61% improvement on Level 2 tasks.




-----

# Fine-tuning

#### [Small Language Models are the Future of Agentic AI (2506.02153v2)](Master%20Thesis%20Papers/Small%20Language%20Models%20are%20the%20Future%20of%20Agentic%20AI%20(2506.02153v2).pdf)
Belcak et al. identify agentic interactions as natural pathways for gathering highly specialized data to iteratively improve SLMs.
- Because agentic sub-tasks demand strict adherence to output formatting (e.g., JSON or Python for tool calls), SLMs can be easily fine-tuned to enforce a single formatting decision, eliminating the overhead required for an LLM to juggle multiple formats.
- The authors outline a continuous **LLM-to-SLM Agent Conversion Algorithm** where initial deployments log prompts and tool calls to build curated datasets. Unsupervised clustering is then used to identify recurring task patterns, which are subsequently used to train specialized SLMs using Parameter-Efficient Fine-Tuning (PEFT) techniques like LoRA or QLoRA . Because SLM fine-tuning requires only a few GPU-hours, agentic behaviors can be rapidly specialized, adapted, or corrected overnight.


#### [Multi-agent Architecture Search via Agentic Supernet](Master%20Thesis%20Papers/Multi-agent%20Architecture%20Search%20via%20Agentic%20Supernet%20(2502.04180v2).pdf) 
- Instead of traditional parameter fine-tuning, Zhang et al. utilize an optimization strategy based on environmental feedback to jointly update the probability distribution of agentic operators and the operators themselves.
- Because agentic operators include black-box tool usage and natural language prompts that cannot be optimized via numerical backpropagation, the authors employ **agent-based textual gradients**. These textual gradients are agent-generated analyses that provide structural updates, prompt refinements, and model temperature adjustments to self-evolve the multi-agent system.
> [!PDF|note] [[Multi-agent Architecture Search via Agentic Supernet (2502.04180v2).pdf#page=5&selection=281,0,283,38&color=note|Multi-agent Architecture Search via Agentic Supernet (2502.04180v2), p.5]]
> > Figure 3. The demonstration of textual gradient.
> 
-  **Cross-Model Transferability of the Tuned Architecture:** The probabilistic routing distribution, once fine-tuned via this cost-constrained optimization, does not overfit to a single model. The authors showed that a supernet optimized using a specific LLM (like GPT-4o-mini) successfully transferred to other backbones (like Qwen-2.5-72b and Llama-3.1-70b), yielding performance improvements of approximately 5%, proving that the optimized orchestration strategy generalizes beyond its specific training environment.
- The optimization of the agentic supernet demonstrates **strong inductive capabilities, meaning the fine-tuned controller can generalize to operators it was never explicitly trained on.** For instance, when the researchers held out the "Debate" operator during training and introduced it only at inference, the tuned system was still able to reasonably activate and utilize it at appropriate proportions.







-----
# Thesis Relevance

#### [Small Language Models are the Future of Agentic AI (2506.02153v2)](Master%20Thesis%20Papers/Small%20Language%20Models%20are%20the%20Future%20of%20Agentic%20AI%20(2506.02153v2).pdf)
- The authors explicitly argue that SLMs are sufficiently powerful, inherently more suitable, and necessarily more economical for agentic systems compared to LLMs. They argue that the dominance of LLMs in agent design is a misallocation of resources, which directly supports your motivation.
- **Decomposition and Narrow Scope:** The paper highlights that agentic applications expose only a very narrow subset of language model capabilities. Because complex goals are decomposed into modular sub-tasks, generalist LLMs are often overkill. This supports your system design where communication is restricted to the orchestrator and specialized sub-agents.
- Efficiency and Scaling: The paper provides a strong foundation for your efficiency research questions, noting that SLMs are 10-30x cheaper in latency, energy consumption, and FLOPs.
- The authors outline an LLM-to-SLM conversion algorithm, emphasizing that organic data gathered from agentic interactions can be used to fine-tune SLMs overnight. This perfectly frames your planned exploration of role-specific fine-tuning.