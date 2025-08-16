---
title: How Modern Optimization Techniques Balance Learning in Deep Neural Network
date: 2025-07-22
tags:
  - optimizer
source: Atli Kosson
draft: true
---
# Main Idea
- Neurons as feature detectors where the direction of $w$ determines which patterns in $x$ the neuron responds to.
	- ==angular update==
	- ==local relative representation change ==
- normalization - makes weights scale-invariant, only ==direction== matters.
	- introduce gains & biases
	- the only meaningful gradient is in the direction percendicular

Learning rate != update size

# The Balanced Learning Hypothesis
==Hypothesis:== Effective learning requires balanced updates

1) Balance across network components (layers/neurons)
	- some neurons hardly updated
	- some neurons change very fast
2) Balance throughout training
	- rapid change at some point 
	- stop learning too early
	- some kind of gini coefficient ?
3) Balance across scale
	- hyper parameters transfer for similar update dynamics
# Part 1: Balance Across Layers
Weight Decay, Normalization, Adam

Weight Decay (decrease magnitude) vs Updates (increase weight magnitude)
- determines the average angular update (x= magnitude, y = direction)
![[Screenshot 2025-07-22 at 10.27.39 PM 1.png]]

## L2 != Weight Decay

# Part 2: Balance Across Time
