---
title: "GPU Programming Fundamentals: A Hardware-First Perspective"
tags:
  - William_Brandon
draft: true
---
1) Deep Learning Compilers
2) LLM efficiency research
3) MIT 6.S894 (Accelerated Computing)

- blocks
- threads per block

streaming multiprocessors (sm)
- 4 things/ partitions/ warp scheduler (32 threads)
- masking for if statement
- threads to keep SM busy = 4 * 32 = 128

Warp Scheduler -> 4 warp scheduler per SM
- functional units
	- 32 bits adder 
	- 64 bits adder

