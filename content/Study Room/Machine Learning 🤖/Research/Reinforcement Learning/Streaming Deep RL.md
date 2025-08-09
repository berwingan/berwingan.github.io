---
title: Streaming Deep RL
draft: false
date: 2025-07-29
source: Rupam Mahmood
tags:
  - streaming
  - continual_learning
---
constrained learning, efficiency

Offline learning vs Online Learning ?

### Online Learning 
- draw randomly from past experience

### Streaming Learning
- use most recent example
- don't store past data

### Why store past experience (raw experience)?
- offline learning is well understood
- memory replay in natural intelligence
- replay allows more information extraction
	- sample efficient

|                              | Non-/Pre- deep RL | Deep RL (NN+GD) |
| ---------------------------- | ----------------- | --------------- |
| Streaming Learning           | TD, Q-Learning    | Q-Learning + NN |
| Batch/ replay-based learning | LSTD, Dyna-Q      | DQN PPO, SAC    |
Streaming learning can get stuck in local minima => ==Stream barrier==

# Cause of Stream Barrier
1) gradient descent is unstable under ==non-stationarity==
2) catastrophic forgetting and loss of plasticity
3) non-stationarity ?

# Remedies
1) Weight Initialization, re-initialization, pertubation/search
2) sparse represen

# Deep Learning Algo: AVG 
Action-Value Gradient -> SAC without replay buffers, target networks, and mini-batch update
1) Observation and TD error normalization
2) Penultimate activation normalization
3) needs tuning
4) 

# Stream-X
1) Sparse initialization
2) layer normalization
3) observation and reward normalization
4) new optimizer for bounding step-size based on update size

# Quantifying Update Size
- overshooting
- bounding step size ?

# Opportunities
1) Model-based RL
2) Exploration
3) Intrinsic motivation
4) Options










