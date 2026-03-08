---
paper id: 2203.11171v4
title: "Self-Consistency Improves Chain of Thought Reasoning in Language Models"
authors: [Xuezhi Wang, Jason Wei, Dale Schuurmans, Quoc Le, Ed Chi, Sharan Narang, Aakanksha Chowdhery, Denny Zhou]
publication date: 2022-03-21T17:48
abstract: "Chain-of-thought prompting combined with pre-trained large language models has achieved encouraging results on complex reasoning tasks. In this paper, we propose a new decoding strategy, self-consistency, to replace the naive greedy decoding used in chain-of-thought prompting. It first samples a diverse set of reasoning paths instead of only taking the greedy one, and then selects the most consistent answer by marginalizing out the sampled reasoning paths. Self-consistency leverages the intuition that a complex reasoning problem typically admits multiple different ways of thinking leading to its unique correct answer. Our extensive empirical evaluation shows that self-consistency boosts the performance of chain-of-thought prompting with a striking margin on a range of popular arithmetic and commonsense reasoning benchmarks, including GSM8K (+17.9%), SVAMP (+11.0%), AQuA (+12.2%), StrategyQA (+6.4%) and ARC-challenge (+3.9%)."
comments: "Published at ICLR 2023. V2: added PaLM results; V3: added UL2 results; V4: camera ready version at ICLR 2023"
pdf: "[[Master Thesis Papers/Self-Consistency Improves Chain of Thought Reasoning in Language Models (2203.11171v4).pdf]]"
url: https://arxiv.org/abs/2203.11171v4
tags: []
---
> [!PDF|yellow] [[Self-Consistency Improves Chain of Thought Reasoning in Language Models (2203.11171v4).pdf#page=1&selection=67,38,75,45&color=yellow|Self-Consistency Improves Chain of Thought Reasoning in Language Models (2203.11171v4), p.1]]
> >  It first samples a diverse set of reasoning paths instead of only taking the greedy one, and then selects the most consistent answer by marginalizing out the sampled reasoning paths. Self-consistency leverages the intuition that a complex reasoning problem typically admits multiple different ways of thinking leading to its unique correct answer. Our extensive empirical evaluation shows that self-consistency boosts the performance of chain-of-thought prompting with a striking margin on a range of popular arithmetic and commonsense reasoning benchmarks, including GSM8K (+17.9%), SVAMP (+11.0%), AQuA (+12.2%), StrategyQA (+6.4%) and ARC-challenge (+3.9%).
> >**in a nutshell**

> [!PDF|yellow] [[Self-Consistency Improves Chain of Thought Reasoning in Language Models (2203.11171v4).pdf#page=4&selection=2,47,5,79&color=yellow|Self-Consistency Improves Chain of Thought Reasoning in Language Models (2203.11171v4), p.4]]
> > One should note that self-consistency can be applied only to problems where the final answer is from a fixed answer set, but in principle this approach can be extended to open-text generation problems if a good metric of consistency can be defined between multiple generations, e.g., whether two answers agree or contradict each other.


