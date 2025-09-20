---
title: "FlexOlmo: Open Language Models for Flexible Data Use"
date: 2025-08-26
source: Sewom Min
tags:
  - MoE
  - transformer
  - ScaleML
---
# Main Idea
How to use MoE to enable training on distributed datasets owned by different parties
1) starting model trained on public data
2) set of local data
3) recombine
# Other Options
1) Model Merging
	1) Model soup
	2) Ensembling
2) MoE merging
	1) add router in front of feed forward network (with seperate FFN from each source)
	2) model soup for other layers (Norm, MHA, Norm)
	3) router needs to train on all data <- problem if ppl want their data to be private

# Solutions
1) Learning to Coordinate 
	1) all distributed source trains two experts, one is frozen , second is being trained. everyone shares the same frozen expert.
2) Nonparametric Router
	- total router size when recombined = $n*h$ .  Where $n-1$ is total number of experts.
	- When training only use $2*h$. One for the frozen part, one of the active expert.
	- ==q==: is there some kind of positional bias ? 

# Question/ Ideas
1) How does the router know which expert to direct to ?
2) What if two experts understand things differently ?
3) Adding different modality ? Vision ? ==open research question== Mixture of Transformers ?
4) Original model to use from is already a mixture-of-expert so instead of freezing 1 expert when training a new one, freeze n-1 experts (the original model).
5) Add a tiny model. Which expert to ==assimilate== the tiny model to.
	1) A “tiny model” could in principle be **aligned via the similarity mechanism** (their $sim(h,r_i)$ scoring), but the **quality of assimilation** would depend on whether the tiny model’s embedding space can be aligned with the anchor’s residual stream
	2) how to make a benchmark ?
6) Freeze the subject expert and do post-merger training for the public anchor model.

# Open Problems
1) Can we make use of fine-grained MoE to enable fine-grained data addition ? 
2) scaling # of experts ?
3) Can we leverage this architecture & training to allow continual learning ?
4) How to better train a nonparametric router ?
5) Harmful expert ?
6) Try using a bunch of tiny llm ? ==to try==
	1) how to make a benchmark for tiny stuff ?
7) use more experts but weighted ? 

Routing
Load Balancing
How to allow people to contribute specialized experts continually?


![[Pasted image 20250826013144.png]]
![[Pasted image 20250826013201.png]]


