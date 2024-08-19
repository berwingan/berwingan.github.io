---
title: Lambda Calculus 🧮
tags:
  - hvm
  - arc-agi
---
These are notes taken from Adam Jones [introduction of Lambda Calculus](https://www.youtube.com/watch?v=b5VhYkvOk30&list=PLoyEIY-nZq_uipRkxG79uzAgfqDuHzot-&index=1)
# Intro to Lambda Calculus
Write an identity function that takes a 3
```Haskell
(\x -> x) 3
```
take x  -> return x
```
(\odd -> odd) 3
```
Literal = 3
Variable = Odd
Abstraction/ Function Definition  =  ( \\odd -> odd)
Application = (\\odd -> odd) 3
## Parts of Expression
```Haskell
(\x -> (\y ->x)) 1 2
(\y -> 1) 2
(2 -> 1)
1
```

### Exercise
```Haskell
(\odd -> odd 3)(\x -> equals (mod x 2 ) 1)
(\x -> equals (mod x 2) 1) 3
equals (mod 3 2) 1
equals 1 1
True
```


**Step 1: Original Expression**
$$
(\lambda x. \lambda y. x \, y) (\lambda z. z)
$$
**Step 2: Apply the function to the argument**
$$
\lambda y. (\lambda z. z) \, y
$$
**Step 3: Simplify the inner expression**
$$
\lambda y. y
$$
**Final Simplified Expression**
$$
\lambda y. y
$$

# Grammar of the Lambda Calculus
```Haskell
e = x        --variable
  | e_1 e_2  --application
  | \x -> e  --abstraction
```


# Free and Bound Variables in Lambda Calculus
1) Function abstraction binds variables
2) Variables that arenot bounds are considered free or unbound

```Haskell
(\x -> x) 3
```
x = bound by function abstraction
3 = unbounded
```Haskell
(\x -> (\z -> y)) h
```
y = unbounded
h = unbounded

## Free Variables Solutions
$FV(x) = \{x\}$  \[variable\]
$FV(e_1\; e_2) = FV(e_1) \;\cup\; FV(e_2)$ \[function application\]
$FV(\\x \rightarrow e)= FV(e) - \{x\}$ \[function abstraction \]

---

$FV((\\z \rightarrow z) y) =FV(\\z \rightarrow z) \;\cup\; FV(y)$
$FV(\\z \rightarrow z) = FV(z) - \{x\}$
$FV(y) = \{y\}$
$FV(z) = \{z\}$

$FV(\\z \rightarrow z) = \{x\} - \{x\}$
$FV((\\z \rightarrow z) y) = \{\} \;\cup\; \{y\}$
$FV((\\z \rightarrow z) y) = \{y\}$

The free variables is only $y$

# Let Expressions in Lambda Calculus
```Haskell
let x = 3 in odd x
(\x -> odd x) 3
```
## Let Expressions and Polymorphism
```Haskell
let x = (\x -> x)
  in x (odd (x 3))
```

```Haskell
e = x        --variable
  | e_1 e_2  --application
  | \x -> e  --abstraction
  | let x = e_1 in e_2 --let
```

# Type Inference 

| Example  | Type                                                           |
| -------- | -------------------------------------------------------------- |
| 3        | Int                                                            |
| True     | Bool                                                           |
| odd      | function from Int to Bool                                      |
| odd 3    | Bool                                                           |
| odd True | not well-typed                                                 |
| \x -> x  | function, which for an $\alpha$ , is from $\alpha$ to $\alpha$ |


# Types in Hindley-Milner
	A type system for the lambda calculus with let statements

1) Type Variables
	1) $\alpha$
	2) $\beta$
2) Type Function Applications
	1) List Bool
	2) Int -> Bool
	3) Bool
	4) $\alpha \rightarrow \alpha$
	5) List $\alpha$
## Monotypes in Hindley-Milner
