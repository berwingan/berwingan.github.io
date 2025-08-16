---
title: Learning Compositional Models of the World
date: 2025-06-10
tags:
  - planning
  - composition
---
1) Energy Optimization
2) Planning
3) Reasoning
# Energy Optimization 
- probability function -> verifier over space of generations
- contrastive loss
- diffusion models
#### Composing Different Energy Functions at Prediction Time 
- independent factors
- product, mixture subtraction

# Planning
- planning with energy minimization
- trajectory energy function, cost function (optimize over both?)
- combining models across domain (language, video, egocentric)
- use video language planning as the search

# Reasoning
- finding a solution x which minimize an energy function
- multi verifiers, compare overall energy function to determine correct
	- test against 1 over N security breaking


Boundaries of stitching chunk