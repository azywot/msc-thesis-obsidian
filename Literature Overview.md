-------

## Table of Contents

- [Multi-Agent System (MAS) and SLMs](#multi-agent-system-mas-and-slms)
  - [MAS Literature](#mas-literature)
  - [Small Agents Literature](#small-agents-literature)
- [Datasets](#datasets)
- [Fine-tuning](#fine-tuning)

---------
# Multi-Agent System (MAS) and SLMs
## MAS Literature

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


## Small Agents Literature
#### [Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools](Master%20Thesis%20Papers/Agentic%20Reasoning%20A%20Streamlined%20Framework%20for%20Enhancing%20LLM%20Reasoning%20with%20Agentic%20Tools%20(2502.04644v2).pdf)
While the primary experiments in this study utilize frontier models like DeepSeek-R1 and DeepSeek-V3, the architectural design strongly supports the principles of Small Language Model (SLM) ensembles. The authors highlight the advantage of **Task-specific model modularity**, which allows different language models to be assigned to different tasks based on their strengths. Specifically, they note that an agentic setup allows for the routing of simpler subtasks—such as summarizing web search results—to lightweight, non-reasoning models. This modularity optimizes resource usage and preserves efficiency by matching the best, potentially smaller, model to each specific subtask rather than relying on a monolithic model for every step.





-----
# Datasets 
#### [Agentic Reasoning A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools](Master%20Thesis%20Papers/Agentic%20Reasoning%20A%20Streamlined%20Framework%20for%20Enhancing%20LLM%20Reasoning%20with%20Agentic%20Tools%20(2502.04644v2).pdf)
- The authors utilize the **GAIA benchmark** to evaluate their system's ability to handle reasoning, web browsing, and tool-use proficiency. Their results on GAIA validate the necessity of multi-agent collaboration for complex tasks; they note that GAIA requires a combination of advanced reasoning and tool-use that benefits heavily from their agentic framework, surpassing prior search-in-reasoning approaches.
- The paper also evaluates expert-level problem-solving using datasets like **GPQA and Humanity's Last Exam,** demonstrating that well-orchestrated agentic systems can close the gap with proprietary, closed-source models on highly difficult, multi-step benchmarks.

-----

# Fine-tuning