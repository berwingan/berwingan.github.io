---
title: "egg: Fast and Extensible Equality Saturation"
draft: true
tags:
  - Max_Willsey
---
- deferred invariant maintenance
- e-class analyses
- e-graph 
- term rewriting
- optimization
	- constant folding, nullability, tensor shape, non-zero, interval arithmetic,
# Equality Saturation
1) Initial Term
2) E-Graph
	1) find a pattern
	2) apply a match
	3) restore invariants
3) Optimized Term


```python
def equality_saturation(expr, rewrites):
    egraph = initial_egraph(expr)
    
    while not egraph.is_saturated_or_timeout():
        for rw in rewrites:
            for (subst, ec) in egraph.ematch(rw.lhs): #read
                ec2 = egraph.add(rw.rhs.subst(subst)) #write
                egraph.merge(ec, ec2)                 #write/ restore invariant
    
    return egraph.extract_best()
```

rewrites earlier in the list can affect later rewrites
# Deferred Invariant Maintenance
1) Initial Term
2) E-Graph
	1) find ==all== pattern
	2) apply ==all== match
	3) restore ==all== invariants
3) Optimized Term

```python
def equality_saturation(expr, rewrites):
    egraph = initial_egraph(expr)
    
    while not egraph.is_saturated_or_timeout():
        matches = []
        for rw in rewrites: #read
            for (subst, ec) in egraph.ematch(rw.lhs):
                matches.append((rw, subst, ec))
                
        for (rw, subst, ec) in matches: #write
            ec2 = egraph.add(rw.rhs.subst(subst))
            egraph.merge(ec, ec2)
            
        egraph.rebuild() #restore invariants
    
    return egraph.extract_best()
```

deferred the restoring.
# Rewriting E-Graphs
$$(a*2)/2$$
# E-Class Analysis
1) attach 1 fact per e-class from a join-semilattice D
2) make(n) -> $d_c$
	- make a new analysis value for a new e-node
3) $\text{join}(d_{c1},d_{c2}) -> d_c$
	- combine two analysis values
4) $\text{modify}(c) -> c'$
	- change the e-class (optionally)

