---
title: How I Understand Flow Matching
draft: true
source: Jia-Bin Huang
date: 2025-07-19
tags:
  - flow
---

1) Normalizing Flows
2) Continuous Normalizing Flows
3) Flow Matching
4) Scaling

# Main Idea
Train a generator that transform a base distribution (noise) into the data distribution using maximum likelihood.


- affine coupling layer
- autoregressive flow
- residual flows

