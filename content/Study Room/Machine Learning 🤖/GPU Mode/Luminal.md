---
title: Luminal - Search-Based Deep Learning Compilers
date: 2025-07-13
draft: false
tags:
  - compiler
  - search
  - kernels
source: Joe Fioti
---
ML Compiler

# Radical Simplification Through Search
1) Matmuls
2) Adds
3) Muls
4) Few Elementwise Ops

# 11 Main
## Unary
1) Exp2
2) Log2
3) Sin
4) Recip
5) Sqrt
## Binary
1) Add
2) Mul
3) Mod
4) LessThan
## Reduction
1) SumReduce
2) MaxReduce

# Ideas
1) Going static
2) Compilers slow by default
3) Complex operation needs many simple operations
4) ML Compilers
	1) Very Large Instruction Width
5) Kernel Search 
6) Use Bend2 ?

![[Pasted image 20250714143730.png]]


# Kernel Search
1) Represent models as graph
2) Convert graphs into egglog expressions
3) Use simple rewrite rules to transform the expression
4) Profile the discovered kernels and choose the fastest
5) Use MCTS to only profile a small subset.

## Question
1) Tolerance for different kernels, some kernels have more multiplies and their floats becomes different numerically. How to maintain stability ? Do it symbolically ?
2) egraphs-good.github.io ?
3) Equality Saturation ?

# Kernel Fusion
Most power is for moving data.
Best to move stuff less = faster compute.

![[Pasted image 20250714162418.png]]

Naive vs Flash Attention
Flash Attention 2 ?
Flash Attention 3 ?

# Post Processing 
1) Buffer Reuse
2) Queueing Kernels

# Pruning
1) Alpha Beta Pruning
2) MCTS
3) Other types ?
4) Use search to determine which basics ops to keep  ?
5) Collective Ops ?


