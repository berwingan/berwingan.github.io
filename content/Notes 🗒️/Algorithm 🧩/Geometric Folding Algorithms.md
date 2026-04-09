---
title: "Geometric Folding Algorithms: Linkages, Origami, Polhedra"
tags:
  - 6_849
  - Erik_Demaine
draft: true
---
# Lecture 1: Overview

## Geometric Objects
1) Linkage
	- rigid bars
	- no crossing
2) Paper
	- no stretch
	- no tears
	- no crossing
3) Polyhedra
	- no overlap
	- one piece

### Questions
1) **Foldability**: what structures fold at all/ in particular way ?
2) **Design**: what shapes (or particular property) can be folded & how ?

### Results:
1) **Universality**: everything can be folded + algorithm
2) **Decision**: efficient algorithm to decide foldability
3) **Hardness**: computationally intractable to decide foldability

### Ideas
1) Linkages
	1) allowing intersection
		- converting linear motion to circular motion
	2) Rigidity: does a linkage given fold at all ? 
	3) Linkages forbidding intersection
		- reconfiguration: fold from config A to config B
		- special linkages
			- chain
			- trees
				- locked trees
2) Paper
	1) Foldability: which crease patterns fold flat ?
	2) Design: what shapes can be folded ?
		1) Origamizer
		2) TreeMaker
	3) Universal Hinge Pattern
3) Polyhedra
	1) Unfolding
		1) edge-unfolding
		2) general unfolding
4) ==Hinged Dissections==
	- take any finite set of polygons of the same area, they can be folded from one chain of polygons without collision
## Open Problems
1) No crossing
2) which 3d chains/2d trees have ''==locked== configurations''
3) Mountain and valley on paper crease to be able to be folded ?
4) Edge-unfolding convex polyhedra

# Lecture 2: Simple Folds

## Origami Terminology
1) Piece of paper = 2d polygon with distinguished top/bottom
2) Crease = line segment or curve drawn on paper
3) Crease Pattern = bunch of creases = planar graph drawn on paper
4) Folded state = finished origami
	1) folded state -> unfold -> crease pattern
5) Flat folding = folded state lying in the plane
	- flat foldable
6) Mountain Crease = bottom sides touch
7) Valley Crease = top sides touch

7:52