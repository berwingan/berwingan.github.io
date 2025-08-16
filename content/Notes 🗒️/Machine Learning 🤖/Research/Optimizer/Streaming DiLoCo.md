---
title: Streaming DiLoCo with overlapping communication
draft: true
tags:
  - distributed
  - speedrun
date: 2025-07-13
source: Arthur Douillard
---

1) Data Parallelism
2) Tensor Parallelism
3) Pipeline Parallelism

- more data
- bigger model
- better algo

Use compression to make the bits smaller
Quantization, ==mix quantization== ?
- sync the smaller bits more ?
- sync the higher bits less ?
- sub-layer quantization.
Update 1/3 or 1/4 the layer at a time.

LoRA ? 
![[Pasted image 20250713004514.png]]

Pruning idea ?
- don't really make sense unless all local models have the same weights that is doing the higher activation (unlikely if data is random between local models)


Classical methods (mathematical equivalent)
Non-classical methods

# Fault resiliency ? 
- GPU  Error
- Method to take the gradients in the next cycle/ update
Experiment with nanoGPT.



![[Pasted image 20250713010453.png]]


==Picotron== Hugging Face


# Question
1) *Are the weights you get from averaging 2 local models the same as the weights you get from 1 local model trained with all the same data if all local models are starting from the same randomize weights ?*
- Averaging Weights Leads to Wider Optima and Better Generalization
- Understanding the Effectiveness of Early Weight Averaging for Training Large Language Models
- GRAWA: Gradient-based Weighted Averaging for Distributed Training of Deep Learning Models
- Model Aggregation Techniques in Federated Learning: A Comprehensive Survey
- Federated Learning: Challenges, Methods, and Future Directions


2) *Distributed learning on vision ?*
3) *non-gradient training ?*

