---
title: Relational Model & Relational Algebra
tags:
  - cmu
  - database
---
[Lecture Slides](https://15445.courses.cs.cmu.edu/fall2023/slides/01-relationalmodel.pdf)
[Lecture Notes](https://15445.courses.cs.cmu.edu/fall2023/notes/01-relationalmodel.pdf)

Database != Database Management System (DBMS)
## Database
	organized collection of inter-related data that models some aspect of the real-world
## Focus
- implementation
- data integrity
- durability

## Data Models Type
1) ==Relational==  -> unordered set, use primary keys to uniquely identify tuple
2) Key/Value
3) Graph
4) Document/ Object
5) Wide-Column/ Column-family
6) Array/ Matrix/ Vectors
7) Hierarchical
8) Network
9) Multi-Value

# Relational Models
1) Primary Keys
2) Foreign Keys
3) Constraints
## Data Manipulation Languages (DML)
1) Procedural ← Relational Algebra
2) Non-Procedural (Declarative) ← Relational Calculus 

# Relational Algebra
Fundamental Operations
1) Select $\sigma$  → where clause
2) Projections $\pi$  →  after select clause
3) Union
4) Intersection
5) Difference → except keyword
6) Product
7) Join
8) Rename
9) Assignment
10) Duplicate Elimination
11) Aggregation
12) Sorting
13) Division


Reading Chapters 1-2