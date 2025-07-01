---
title: "STP: Self-Play LLM Theorem Provers with Iterative Conjecturing and Proving"
date: 2025-06-28
source: Prof Tengyu Ma
tags:
  - self-play
  - agents
---

Reasoning ~ coding + math

"Classical" reasoning = brute force search-base
LLM
- pattern matching
- hallucination
- self-reflection
- extract vague intuition from few-show examples
- incapability of long, precise mechanical deduction (tool use)

# Issues 
- Lack-of-Data for proofs
- how did human mathematicians developer intuition with lack of data.
- practice on variants/ extensions of known theorems
	- make statement more abstract
	- Conjecturer dataset
		- can't be ==too easy== (1-8/32) tries
	- Prover dataset
		- correct and non-trivial
- Elegancy score: $\frac{\text{Length of shortest correct proof}}{\text{Length of the conjecture}}$
- Diversity across different domains of math




# Question
1) Ablation study on how different domains of the dataset affects end ability ?
2) Re-weighting the domains of dataset ?
3) What makes a problem novel compared with existing dataset ?