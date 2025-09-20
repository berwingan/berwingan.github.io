---
title: AlphaZero
draft: true
---
function (state) -> (policy, value)
# MCTS
1) Selection - walk down until leaf node
2) Expansion - create new node
3) Simulation - play randomly
4) Back-propagation

Upper Confidence Bound (UCB) Formula
# Alpha MCTS
1) Selection
2) Expansion
3) Back-propagation

Updated UBC Formula

Keep track of 
1) Total action value (sum of simulation results)
	1) NN output policy head and value head
2) Number of visits
3) Prior Probability