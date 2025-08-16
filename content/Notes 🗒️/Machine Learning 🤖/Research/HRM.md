---
title: Hierarchical Reasoning Model
date: 2025-07-29
tags:
  - hierarchy
source: https://arxiv.org/pdf/2506.21734
---
# Components

| Component         | Architectural                   |
| ----------------- | ------------------------------- |
| Input Processing  | Standard Embedding Layer        |
| Low-Level Module  | Encoder-Only Transformer Block  |
| High-Level Module | Encoder-Only Transformer Block  |
| Output Processing | Standard Linear Layer + Softmax |

# Responsibility
1) H-Module -> directs overall problem-solving strategy
2) L-module -> executes the intensive search or refinement

forward residual ?
full self-attention
Adaptive Computation Time Mechanism  -> control over H-Module and L-Module
'recurrent' = cycle in graph

# Deep Supervision
- break forward passes into smaller passes <- how ?
	- takes per segment step ?

# Adaptive Computation Time (ACT)
- How many segment to run module for ?
- act as a RL agent ???????
	- Q-Head
		1) Q-Halt: expected reward if we stop thinking now and give the current answer
		2) Q-Continue: expected reward if we spend more computation and run for another segment
	- Decision Rule: Q-Halt > Q-Continue


# The Recurrent Operations
1) Low-Level Module takes T steps (==T== is definitely learnable)
2) High-Level Module takes 1 steps
3) Repeat

# To Read
1) Universal Transformer