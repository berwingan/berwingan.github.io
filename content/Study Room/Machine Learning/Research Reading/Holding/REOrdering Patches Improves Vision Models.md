---
title: REOrdering Patches Improves Vision Models
date: 2025-06-15
tags:
  - vision
  - transformer
---
Order which images are converted from 2-D grid into 1-D sequences of patches
1) row-major
2) column major
3) Hilbert curves
4) Spiral
5) Diagonal
6) Snake

Transformers as sequence models for vision.
Self-Attention + Positional Embeddings =. Permutation-Equivariant.
Inductive biases = locality, recurrence, input-dependent state dynamics
Sparse Attention
Plackett-Luce ranking model

1) Image transformer -> self attention on local neighborhoods of patches
2) Vision Transformer (ViT) -> global self-attention
	- $O(n^2)$ operation in computation and space
	- not efficient
		1) Sparse Attention
		2) Longformer
		3) Transformer-XL
		4) Mamba & ARM
3) Hierarchical tokenization
	- process image at multiple scales to reduce sequence length at higher levels
4) Specific order for sequence

**Key Idea**: Patch Order Sensitivity
- long context model forget stuff in NLP
- Use RL to rank patches permutation to find most effective
# Preliminaries
1) Permutation equivariance of full self-attention not desired for vision
	- positional embeddings (Transformer-XL)
		- absolute
		- native relative
2) 

![[Pasted image 20250615224544.png]]
# Does Patch Order Matter ?


# Reference To Follow Up
1) Understanding and improving robustness of vision transformers through patch-based negative augmentation
2) 
