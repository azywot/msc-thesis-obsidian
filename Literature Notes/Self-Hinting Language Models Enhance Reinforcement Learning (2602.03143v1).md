---
paper id: 2602.03143v1
title: Self-Hinting Language Models Enhance Reinforcement Learning
authors:
  - Baohao Liao
  - Hanze Dong
  - Xinxing Xu
  - Christof Monz
  - Jiang Bian
publication date: 2026-02-03T05:56
abstract: Group Relative Policy Optimization (GRPO) has recently emerged as a practical recipe for aligning large language models with verifiable objectives. However, under sparse terminal rewards, GRPO often stalls because rollouts within a group frequently receive identical rewards, causing relative advantages to collapse and updates to vanish. We propose self-hint aligned GRPO with privileged supervision (SAGE), an on-policy reinforcement learning framework that injects privileged hints during training to reshape the rollout distribution under the same terminal verifier reward. For each prompt $x$, the model samples a compact hint $h$ (e.g., a plan or decomposition) and then generates a solution $τ$ conditioned on $(x,h)$. Crucially, the task reward $R(x,τ)$ is unchanged; hints only increase within-group outcome diversity under finite sampling, preventing GRPO advantages from collapsing under sparse rewards. At test time, we set $h=\varnothing$ and deploy the no-hint policy without any privileged information. Moreover, sampling diverse self-hints serves as an adaptive curriculum that tracks the learner's bottlenecks more effectively than fixed hints from an initial policy or a stronger external model. Experiments over 6 benchmarks with 3 LLMs show that SAGE consistently outperforms GRPO, on average +2.0 on Llama-3.2-3B-Instruct, +1.2 on Qwen2.5-7B-Instruct and +1.3 on Qwen3-4B-Instruct. The code is available at https://github.com/BaohaoLiao/SAGE.
comments: ""
pdf: "[[Self-Hinting Language Models Enhance Reinforcement Learning (2602.03143v1).pdf]]"
url: https://arxiv.org/abs/2602.03143v1
tags: []
---
> [!PDF|yellow] [[Self-Hinting Language Models Enhance Reinforcement Learning (2602.03143v1).pdf#page=1&selection=287,0,290,58&color=yellow|Self-Hinting Language Models Enhance Reinforcement Learning (2602.03143v1), p.1]]
> > Existing remedies largely modify data collection. A common baseline is to skip uninformative updates (e.g., degenerate groups) and resample prompts, which improves performance but implicitly biases training toward easier prompts

