---
title: Muon - An optimizer for hidden layers in neural networks
date: 2025-06-18
tags:
  - optimizer
source: https://kellerjordan.github.io/posts/muon/
---
# Muon
Muon = Momentum ==Orthogonalized== by Newton-Schulz
For 2D parameters ?

```python
def newtonschulz5(G, steps=5, eps=1e-7): 
	assert G.ndim == 2 
	a, b, c = (3.4445, -4.7750, 2.0315) 
	X = G.bfloat16() 
	X /= (X.norm() + eps) 
	if G.size(0) > G.size(1): 
		X = X.T 
	for _ in range(steps): 
		A = X @ X.T 
		B = b * A + c * A @ A 
		X = a * X + B @ X 
	if G.size(0) > G.size(1): 
		X = X.T 
	return X
```

Orthogonal when the dot product is 0. ==Turn== 90 ish degree.
Remove reinforcing component and focus on directions that are geniunly different from what we already have.
Without orthogonalization, if your parameters are [1000, 0.001] and momentum is [500, 0.0005], most of the momentum just reinforces the already-large first parameter.

	don't let the momentum update be biased towards reinforcing the current parameter magnitudes. Instead, focus on directions that are independent of what we already have.

# Alternatives
1) SVD
2) Coupled Newton iteration


# MuonClip
QK-Clipping
Constraint attention scores by rescaling Q/K matrices.
After each Muon step, check QK scores and rescales if it exceed threshold.
==QK== : raw [[Attention Is All You Need |attention]] scores computed before applying softmax in the attention mechanism. Determine how much each position in the sequence should "attend to" every other position.

# Extra
1) NanoGPT-speedrun? CIFAR-10 speedrun ?
2) MuonClip by Kimi



