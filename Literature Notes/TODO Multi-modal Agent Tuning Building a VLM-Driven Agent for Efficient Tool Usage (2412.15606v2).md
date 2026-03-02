---
paper id: 2412.15606v2
title: "Multi-modal Agent Tuning: Building a VLM-Driven Agent for Efficient Tool Usage"
authors: [Zhi Gao, Bofei Zhang, Pengxiang Li, Xiaojian Ma, Tao Yuan, Yue Fan, Yuwei Wu, Yunde Jia, Song-Chun Zhu, Qing Li]
publication date: 2024-12-20T07:00
abstract: "The advancement of large language models (LLMs) prompts the development of multi-modal agents, which are used as a controller to call external tools, providing a feasible way to solve practical tasks. In this paper, we propose a multi-modal agent tuning method that automatically generates multi-modal tool-usage data and tunes a vision-language model (VLM) as the controller for powerful tool-usage reasoning. To preserve the data quality, we prompt the GPT-4o mini model to generate queries, files, and trajectories, followed by query-file and trajectory verifiers. Based on the data synthesis pipeline, we collect the MM-Traj dataset that contains 20K tasks with trajectories of tool usage. Then, we develop the T3-Agent via \\underline{T}rajectory \\underline{T}uning on VLMs for \\underline{T}ool usage using MM-Traj. Evaluations on the GTA and GAIA benchmarks show that the T3-Agent consistently achieves improvements on two popular VLMs: MiniCPM-V-8.5B and {Qwen2-VL-7B}, which outperforms untrained VLMs by $20\\%$, showing the effectiveness of the proposed data synthesis pipeline, leading to high-quality data for tool-usage capabilities."
comments: "ICLR 2025, https://mat-agent.github.io/"
pdf: "[[Master Thesis Papers/Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf]]"
url: https://arxiv.org/abs/2412.15606v2
tags: []
---
 #multimodal #agent #fine_tuning


> [!PDF|yellow] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=1&selection=400,74,402,32&color=yellow|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.1]]
> > Based on the data synthesis pipeline, we collect the MM-Traj dataset that contains 20K tasks with trajectories of tool usage.
> 
> **[NOTE] Dataset link:** https://huggingface.co/datasets/PengxiangLi/MAT

> [!PDF|yellow] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=2&selection=21,0,30,83&color=yellow|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.2]]
> > In this paper, we propose a multi-modal agent tuning method that automatically generates a large number of multi-modal tasks with tool-usage trajectories and tunes a vision-language model (VLM) (Liu et al., 2024b; Chen et al., 2024d; Yao et al., 2024) as the controller for powerful tool-usage reasoning. Compared with LLM-driven agents, VLM-driven agents can utilize multi-modal information (such as required knowledge domains in the multi-modal data) instead of only using the query for reasoning, benefiting efficient tool usage (Liu et al., 2024c; Wang et al., 2024a; Sun et al., 2024). Many efforts are made to enhance specific capabilities of VLMs via finetuning, such as the chain-of-thought ability (Hu et al., 2024), grounding ability (Peng et al., 2023), and feedback-refining ability (Li et al., 2024). This inspires us to construct a large number of multi-modal tool-usage data for VLM-driven agents, which improves the reasoning ability when using tools for real-world tasks.


> [!PDF|red] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=2&selection=54,0,76,84&color=yellow|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.2]]
> > With the data generation pipeline, we construct MM-Traj, a dataset that contains 20K multi-modal tasks with tool-usage trajectories. Based on MM-Traj, we introduce the T3-Agent, a VLM-driven agent in the ReAct framework (Yao et al., 2023). The VLM controller of the T3-Agent is developed via T rajectory T uning for Tool usage using MM-Traj. We conduct comprehensive evaluations of the T3-Agent on the GTA (Wang et al., 2024b) and GAIA benchmarks (Mialon et al., 2023), where two popular VLMs are used as the controller, that is MiniCPM-V-8.5B (Yao et al., 2024) and Qwen-VL- 7B (Wang et al., 2024c). The T3-Agent consistently achieves improvements on the two VLMs and outperforms the untrained VLMs by 20%. This indicates that our multi-modal agent tuning method enables agents a powerful tool-usage capability for complex and diverse trajectories
> **[NOTE] try the MM-Traj dataset and VLM as the controller**

> [!PDF|yellow] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=3&selection=44,0,75,103&color=yellow|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.3]]
> > 2.2 TOOL-USAGE DATASET Several tool-usage datasets have been established for agents, such as APIBank (Li et al., 2023), Toolalpaca (Tang et al., 2023), ToolBench (Qin et al., 2023), AnyTool (Du et al., 2024), agentohana (Zhang et al., 2024a), APIGen (Liu et al., 2024d), and AgentInstruct (Zeng et al., 2023). The above datasets contain little multi-modal data (e.g., images, videos, and audios) that are commonly encountered in the real world. Thus, to evaluate the performance of agents in solving multi-modal tasks, some multimodal agent benchmarks have been built, such as the GUI benchmarks: OSWorld (Xie et al., 2024) and MMInA (Zhang et al., 2024b), multi-modal question answering benchmarks: GAIA (Mialon et al., 2023), GTA (Wang et al., 2024b), and m&m’ (Ma et al., 2024), and comprehensive benchmarks: AgentBench (Liu et al., 2023b) and AgentGym (Xi et al., 2024). In addition, some efforts are paid to synthesize trajectory data using LLMs to improve the tool-usage ability of multi-modal agents. DEDER (Choi et al., 2024) resorts to in-context learning to generate trajectories, through which the chain-of-thought reasoning ability is distilled from LLMs to a small model. Lumos (Yin et al., 2024) converts ground-truth reasoning steps in existing benchmarks into the expected format of tool-usage trajectories. TASKBENCH (Shen et al., 2023) samples trajectories from a predefined graph, and then generate queries. MLLM-Tool (Wang et al., 2024a) and LLaVA-plus (Liu et al., 2023a) collect trajectories based on image and tool descriptions. VisualAgentBench (Liu et al., 2023b) manually designs trajectory templates to collect data. Different from the above methods that usually focus on simple and predefined trajectories, or rely on queries in off-the-shelf datasets, our data collection pipeline does not have any constraints, which generates diverse tasks and complex trajectories, improving the volume, complexities, naturalness, and diversity of the tool-usage dataset.
> 
> **[NOTE] Agentic, tool-focused benchmarks; maybe use some of them? Q: which ones?**

> [!PDF|yellow] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=7&selection=1,0,33,50&color=yellow|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.7]]
> > Table 1: Used tools in the T3-Agent Tool name Tool description Web search Perform complicated web browsing to answer a question Image question answering Answer questions for queries based on attached images File inspector Answer questions for queries based on given files Visual segmentation Do instance segmentation on the given image Object localization Localize objects in given images and output the bounding boxes Image generation Create an image according to a textual prompt Image editing Edit image based on the textual prompt Face detection Detect human faces in given images and output the bounding boxes Python package Various packages such as ‘matplotlib’ and ‘opencv’
> 
> **[NOTE] For multimodal data, maybe we should consider adding one of these tools? At least Image QA**

> [!PDF|red] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=7&selection=142,0,147,50&color=red|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.7]]
> > Note that, in training VLMs, we do not use the final answer A, as we encourage the controller to leverage tools in solving given tasks, instead of directly producing an answer based on its internal knowledge. After training, we obtain the T3-Agent.
> 
> **[NOTE] Once we consider fine-tuning some SLM, it’s nice to have it back in mind - if it’s tool-focused, then maybe it’s better to not include the answer.**



> [!PDF|red] [[Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2).pdf#page=8&selection=154,0,154,7&color=red|Multi-modal Agent Tuning Building a VLM-Driven Agent for Efficient Tool Usage (2412.15606v2), p.8]]
> > Level 3
> 
> **[NOTE] !!! Nice to see other setups struggling with Level 3 too :)**
> Also, look at the other models, very interesting
Also, look at the GAIA splits, they seem wrong in the paper…



