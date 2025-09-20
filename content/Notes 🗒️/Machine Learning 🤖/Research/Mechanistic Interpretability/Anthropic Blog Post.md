---
title: Anthropic Blog Post
draft: true
---
# A Mathematical Framework for Transformer Circuits

1) Attention Head
	- Induction Head
		- delete info by writing ==negative== version
	- Independent and Additive
	- Information Movement
		- copy information from the residual stream of one token to the residual stream of another ==????==
		- which token to move information != what information is 'read' to be moved != how it is 'written' to destination
2) Virtual Weights
3) Residual Stream
	- clearing it by reading then writing the negative version
4) Privileged Basis vs Basis Free
5) Each head can learn to choose which linear combination of residual stream (subspace)
	1) read via KVQ
	2) write (PCA, SVD, probing directions)
6) Bottleneck activations
	- embedding size of token is limiting factor in residual stream for passing information



==stopped== at  Observations about Attention Heads
