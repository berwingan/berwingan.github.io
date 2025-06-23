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
3) ==Hierarchical tokenization==
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
Compression % reduction ?
- LZMA, identify repeating patterns and reusing earlier parts of the sequence encode later parts more efficiently ?

# Learning an Optimal Patch Ordering with REOrder
optimal ordering for each model-dataset pair
sequence compressibility vs downstream performance
more similar content = more compressible = not as good ? sometimes

1) discretize images using a VQ-VAE based model 
2) encode resulting token sequence codes using unigram and bigram tokenization
3) measure compression ratio by LZMA

### Q: what else is needed other than compression ratio ? Model specific ?

# Learning to Order Patches
stochastic policy learning problem
policy => distribution over permutations
REINFORCE algorithm - Plackett-Luce policy (ordered decisions)
- salient patches are moved to the end of the sequence ? more relevant to identify


Longformer not really affected because it is already near full attention




## Information-Theoretic Initialization



# Reference To Follow Up
1) Understanding and improving robustness of vision transformers through patch-based negative augmentation
2) 


# Question
1) ==generalizability of REOrder policy==
	1) meta-learning
2) REOrder for other task
	1) object detection
	2) segmentation <- def not likely
	3) captioning
	4) spatially sensitive tasks
	5) multi-label
	6) dense prediction
	7) visual reaosning
3) Differentiable or more efficient ordering
	1) Replace REINFORCE with Gumbel-Sinkhorn, softsort, differentiable sorting
	2) 
4) Dynamic reordering at inference time
	1) adaptively reorder patches at inference time based on partial activations ?
		1) lightweight model that reorders its input patches based on intermediate saliency predictions
		2) can this be done efficiently, using early layers or auxiliary heads ?
5) Relationship between patch order and model inductive bias
6) Self-supervision or contrastive or reconstruction loss
	1) DINO-style pretraining
7) spatio-temporal transformers
	1) VideoMAE, CLIP
8) ==Curriculum learning via patch ordering ==?
	1) go in reverse from what the policy learn.
	2) faster training ?
	3) step size ?