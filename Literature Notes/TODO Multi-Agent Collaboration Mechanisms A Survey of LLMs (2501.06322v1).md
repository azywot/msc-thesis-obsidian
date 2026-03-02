---
paper id: 2501.06322v1
title: "Multi-Agent Collaboration Mechanisms: A Survey of LLMs"
authors:
  - Khanh-Tung Tran
  - Dung Dao
  - Minh-Duong Nguyen
  - Quoc-Viet Pham
  - Barry O'Sullivan
  - Hoang D. Nguyen
publication date: 2025-01-10T19:56
abstract: "With recent advances in Large Language Models (LLMs), Agentic AI has become phenomenal in real-world applications, moving toward multiple LLM-based agents to perceive, learn, reason, and act collaboratively. These LLM-based Multi-Agent Systems (MASs) enable groups of intelligent agents to coordinate and solve complex tasks collectively at scale, transitioning from isolated models to collaboration-centric approaches. This work provides an extensive survey of the collaborative aspect of MASs and introduces an extensible framework to guide future research. Our framework characterizes collaboration mechanisms based on key dimensions: actors (agents involved), types (e.g., cooperation, competition, or coopetition), structures (e.g., peer-to-peer, centralized, or distributed), strategies (e.g., role-based or model-based), and coordination protocols. Through a review of existing methodologies, our findings serve as a foundation for demystifying and advancing LLM-based MASs toward more intelligent and collaborative solutions for complex, real-world use cases. In addition, various applications of MASs across diverse domains, including 5G/6G networks, Industry 5.0, question answering, and social and cultural settings, are also investigated, demonstrating their wider adoption and broader impacts. Finally, we identify key lessons learned, open challenges, and potential research directions of MASs towards artificial collective intelligence."
comments: ""
pdf: "[[Master Thesis Papers/Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf]]"
url: https://arxiv.org/abs/2501.06322v1
tags: []
---
#survey #agent #to_read #survey #MAS
> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=2&selection=76,0,97,73&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.2]]
> > One of the main focus for effective MASs is the mechanisms of collaboration [33, 74, 75 , 97 , 132 ], which lead to a transition from traditional, isolated models toward approaches that emphasize interactions, enabling agents to connect, negotiate, make decisions, plan, and act jointly, driving forward the capabilities of AI in collective settings. A deeper understanding of how collaboration mechanisms operate in MASs is critical to unlocking their full potential.
> 
> **[NOTE] What if we had one sub agent continuously writing to the external memory and then other subagents would have the access to this memory? Like a mind map but for all the subagents**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=4&selection=116,30,121,38&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.4]]
> > This work aims to provide a comprehensive view of the collaborative foundations between LLM-based agents in multi-agent collaborative systems. With collaboration as the main focus, our study characterizes collaborations between agents based on their actors (agents involved), type (e.g., cooperation, competition, or coopetition), structure (e.g., peer-to-peer, centralized, or distributed), and strategy (e.g., role-based, rule-based, or model-based), and the coordination layer in collaborations. 
> 
> **Key idea: paper topic!**

> [!PDF|note] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=4&selection=127,0,156,66&color=note|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.4]]
> > Our main contributions are listed as follows: • Collaborative Aspects and Mechanisms in LLM-based MAS: we focus on the operational mechanisms of LLM-based multi-agent collaboration, emphasizing the "know-how" required to enable effective collaboration, including the collaboration type, strategy, communication structure and coordination architecture. • General Framework for LLM-based MAS: we present a comprehensive framework, integrating diverse characteristics of MAS, allowing researchers to understand, design and develop multi-agent collaborative systems. • Review of Real-World Applications: we examine real-world implementations of LLMbased MASs across various domains, highlighting their practical applications, successes, and limitations. • Discussion of Lessons Learned and Open Problems: we identify key challenges in the developmental agenda of MASs, such as collective reasoning and decision-making, and outline potential research directions to address these challenges.
> 
> **Main contributions**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=5&selection=48,0,49,8&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.5]]
> > Organization: Agents either have hierarchical control or organize based on emergent behaviors.
> 
> **so far ours is hierarchical (orchestrator + sub agents)**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=6&selection=35,0,42,2&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.6]]
> > The defining characteristic of LLMs is their size and the phenomenon of emergent abilities, which arise when models exceed a certain threshold in terms of parameters. These emergent behaviors allow LLMs to solve tasks they were not explicitly trained on, such as analogical reasoning and zero-shot learning, where the model can tackle new problems without additional fine-tuning [ 113 ].
> 
> **[NOTE] emergent abilities - maybe worth studying in the smaller setup (i.e. falure modes)**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=6&selection=64,3,68,9&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.6]]
> > While LLMs have shown remarkable performance in single-agent tasks, their limitations become apparent in multi-agent settings where the complexity of coordination, communication, and decision-making is higher. Issues such as cascading hallucinations — where one erroneous output leads to compounding mistakes pose challenges in sustained multi-agent interactions. 
> 
> **LLM - failure modes**

> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=7&selection=28,76,30,43&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.7]]
> > MASs are interested in agents, or AI models, that can learn, adapt, and collaborate with one another in complex environments, towards a common shared goal.
> 
> [NOTE] Main MAS goal

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=8&selection=191,42,203,72&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.8]]
> > For instance, a straightforward collaboration mechanism is majority voting, similar to ensemble learning. Collaboration can occur at different stages: (i) late-stage collaborations, such as ensembling outputs/actions 𝑦 towards collaborative goals, (ii) mid-stage collaborations, for example, exchanging parameters or weights of multiple models 𝑚 in federated and privacy-preserving manners, and (iii) early-stage collaborations include but not limited to sharing data, context, and environment for model development.
> 
> **[NOTE] Collaboration stages: late- mid- early- stage**

> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=10&selection=35,63,49,29&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.10]]
> >  Our central focus in this framework is the collaboration channels C between agents that facilitate coordination and orchestration among agents. These channels are characterized by their actors (agents involved), type (e.g., cooperation, competition, or coopetition), structure (e.g., peer-to-peer, centralized, or distributed), and strategy (e.g., role-based, rule-based, or model-based). Collaboration mechanisms span various levels of machine learning processes, including data exchange, shared input embeddings, model sharing, and output sharing, enabling agents to interact effectively and leverage each other’s strengths. For each component, we discuss the prevailing implementation trends and methodologies observed in the literature. We examine how these methods align with our proposed framework. We summarize our main findings and lessons learned at the end of the section, offering guidance for future research in the field.
> 
> **[NOTE] MAIN OVERVIEW OF THE PAPER**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=10&selection=93,83,100,70&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.10]]
> > For instance, in [ 117 ], a feedback loop is carried out as the main collaboration channel, where the task is first handled by an LLM model (Actor), then an Evaluator and Self-Reflection model rates the output and results, producing verbal guidance for the Actor to improve
> 
> **[NOTE] Maybe I could add this to the framewrok i have now?**

> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=11&selection=192,0,202,42&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.11]]
> > There are recent open-source frameworks allowing for experimentation with cooperative LLMbased MASs. CAMEL [ 74] provides a role-playing framework where a task-specific agent and two cooperating AI agents (User and Assistant) work to complete tasks via role-based conversations. Similarly, AutoGen [134] enables developers to define flexible agent behaviors and communication patterns, allowing LLM agents to cooperate through conversation and tackle complex tasks by decomposing them into manageable subtasks.
> 
> **MAAS cooperation**

> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=12&selection=139,0,142,52&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.12]]
> > The competitive approach offers advantages such as promoting robustness, strategic adaptability, and complex problem-solving capabilities within MASs. However, competition can also introduce challenges, including potential conflicts that require mechanisms to ensure that competition remains constructive and beneficial to overall system goals.
> 
> **[NOTE] Could we explore this in any way for the thesis?**
> > [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=12&selection=149,34,150,79&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.12]]
> >  In settings where cooperation is desired, excessive competition may hamper alignment, requiring frameworks to balance these aspects effectively
> 
> **I guess we should not**

**[NOTE] Maybe we could explore Coopetition instead?** (As in, MoE for example, that falls under this).


> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=14&selection=190,0,191,1&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.14]]
> > Role-based Protocols.
> 
> **[NOTE] this is what we’re using now**

> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=16&selection=185,0,203,18&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.16]]
> > Centralized Structure. The centralized structure (also known as a star structure) is an implementation where every agent is connected to a central agent. In a centralized structure, the collaboration channels C = {𝑐 𝑗 } are set as the participating-serving nature in a centralized communication channel. 
> 
> **[NOTE] This is what I’m using rn**


> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=19&selection=140,21,161,44&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.19]]
> > DyLAN. This setup facilitates dynamic interactions, incorporating features like inference-time agent selection and an early-stopping mechanism, which collectively enhance the efficiency of cooperation among agents. [74 ] have conceptualized assemblies of agents as a group and focused on exploring the potential of their cooperation [ 18, 41, 105 , 132 ] found social behaviors autonomously emerge within a group of agents
> 
> **emerging social behaviours - insightful**

> [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=20&selection=66,0,73,27&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.20]]
> > The rise of LLM-based multi-agent collaborative systems has been driven by the introduction of LLMs and their effectiveness as central processing brains. Inspired by human collaboration, these systems typically break complex tasks into subtasks, with agents assigned specific roles (e.g., software engineer) to focus on subtasks relevant to their expertise. Collaboration channels are critical in enabling agents to work together, facilitating capabilities such as planning and coordination. These channels are characterized by their actors (agents involved), type (e.g., cooperation, competition, or coopetition), structure (e.g., peer-to-peer, centralized, or distributed), and strategy (e.g., role-based, rule-based, or model-based)
> 
> **[NOTE] nice for thesis intro!**
> > [!PDF|yellow] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=21&selection=33,0,47,15&color=yellow|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.21]]
> > Effective Collaboration Channels: establishing robust collaboration channels among agents is crucial for seamless collaboration. Clear protocols prevent misunderstandings and ensure efficient information exchange. As shown in AutoGen framework [ 134 ] MASs can outperform single-agent systems with effectively designed collaboration mechanisms. On the other hand, as studied in [128 ] MAS approach with suboptimal design for their competitive collaboration channels can be overtaken by single-agent counterpart with strong prompts.


> [!PDF|red] [[Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1).pdf#page=28&selection=64,0,70,67&color=red|Multi-Agent Collaboration Mechanisms A Survey of LLMs (2501.06322v1), p.28]]
> > Discovering/Exploring Unexpected Generalization. Complex, emergent behaviors of collective intelligence, such as coordinated problem-solving or innovation, can arise under the right conditions, especially in generalizing to unseen domains. However, identifying and fostering these conditions is an ongoing challenge. Understanding how these generalizations emerge from the interactions of agents is key to acquiring collective intelligence.
> 
> **[NOTE] to look into this in the thesis**

