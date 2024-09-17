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
$$
\begin{align}
\tau = \alpha \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;[variable]\\
|\;C\;\tau_1\;\dots\;\tau_n\;\;[application]
\end{align}
$$
where $C$ is the set of type functions, which must contain ->
For example $C$= -> , Int, Bool, List, Map, 2-Tuple, 3-Tuple

### For-all Quantifiers
$\forall\alpha.\;\alpha\rightarrow\;\alpha$
```TypeScript
<T>(arg: T): T
```
```Python
T = TypeVar('T')
Callable[[T],T]
```

$\forall\alpha.\;\alpha\rightarrow\;\alpha$
$\beta\;\rightarrow\;\beta$

```Haskell
id (odd (id 3))
```

## Hindley-Milner Types Syntax

$$
\begin{align}
\tau = \alpha \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;[variable]\\
|\;C\;\tau_1\;\dots\;\tau_n\;\;[application]
\end{align}
$$
$$
\begin{align}
\sigma=\tau\;\;\;\;\;\;\;\;\;[monotype]\\
|\;\forall\alpha.\;\;\sigma\;[quantifier]
\end{align}
$$


# Assignments, Contexts, Typing Judgement and Rules in Type Systems
Expression : Type
Assignment = $e:\sigma$
Age : Int

```Haskell
age :: Int
```

context = $\Gamma$ -> a list of assignments
$\Gamma=$
$\;\text{age}:\text{Int},$ 
$\;\text{odd}:\text{Int}\rightarrow\text{Bool}$

age is an integer contained in the context
$\text{age}:\text{Int}\in\Gamma$


$\Gamma = \text{(empty)}$
$\;\;\;\;|\;\Gamma,e:\sigma$

## Typing Judgements
	when an assignment follows given the context, we can make a typing judgement

$\Gamma\vdash e:\sigma$

From the context gamma, the ==expression== e has ==type== $\sigma$

| Context                                                                                     | Judgements                                                                      |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| $\Gamma=$<br>$\;\text{age}:\text{Int},$ <br>$\;\text{odd}:\text{Int}\rightarrow\text{Bool}$ | $\Gamma\vdash\text{age}:\text{Int}$<br>$\Gamma\vdash\text{odd age}:\text{Bool}$ |
Premise => Conclusion (judgement)
$x:\sigma\in\Gamma$ => $\Gamma\vdash\; x:\sigma$

# Free and Bound Type Variables in Type Systems
## Free Variables in Types
$FV(\alpha)=\{\alpha\}$ [var]
$FV(C\;\tau_1\cdots\tau_n)= FV(\tau_1) \;\cup\; \cdots \;\cup\; FV(\tau_n)$ [app]
$FV(\forall\alpha.\sigma)=FV(\sigma)-\{\alpha\}$ [quantifier]
## Free Variables in Contexts
$FV((\text{empty}))=\{\}$
$FV(\Gamma,e:\sigma)=FV(\Gamma)\;\cup\;FV(\sigma)$

### Exercise 1
What are the free variables in this type ?
$\forall\beta.\;\text{List}\;(\beta\rightarrow(\gamma\rightarrow\beta))$

Use rules
$FV(\forall\beta.\;\text{List}\;(\beta\rightarrow(\gamma\rightarrow\beta)))$
$=FV(\text{List}(\beta\rightarrow(\gamma\rightarrow\beta)))-\{\beta\}$    by quantifier: $\sigma=\text{List}\;(\beta\rightarrow(\gamma\rightarrow\beta)),\alpha=\beta$
$=FV(\beta\rightarrow(\gamma\rightarrow\beta))-\{\beta\}$             by app: $C=\text{List},\tau_1=\beta\rightarrow(\gamma\rightarrow\beta)$
$=(FV(\beta)\;\cup\;FV(\gamma\rightarrow\beta)) -\{\beta\}$                  by app: $C=\rightarrow,\tau_1=\beta,\tau_2=\gamma\rightarrow\beta$
$=(FV(\beta)\cup FV(\gamma)\cup FV(\beta)) -\{\beta\}$
$=(\{\beta\}\cup\{\gamma\}\cup\{\beta\})-\{\beta\}$
$=\{\beta,\gamma\}-\{\beta\}$
$=\{\gamma\}$

# Substitutions in Logic
	 A map from variables to terms

$S=\{h\mapsto j,o\mapsto y\}$
$S(\text{hello})=\text{jelly}$

# Applying Substitutions to Type Systems
$S=\{\alpha\mapsto \text{Int}\}$
$S(\alpha\rightarrow\text{Bool})=\text{Int}\rightarrow\text{Bool}$


$S=\{\alpha\mapsto\beta,\beta\mapsto\text{Int}\}$
$S(\alpha\rightarrow\beta)=\beta\rightarrow\text{Int}$
$S(S(\alpha\rightarrow\beta))=\text{Int}\rightarrow\text{Int}$

# Combining Substitutions in Logic
$S_1=\{\alpha\mapsto\gamma,\beta\mapsto\delta\}$
$S_2=\{\alpha\mapsto\beta\}$
$\text{combine}(S_1,S_2)(thing) = S_1(S_2(thing))$
$\text{combine}(S_1,S_2)=\{\alpha\mapsto\delta,\beta\mapsto\delta\}$

# Unifying Substitutions and the Unification Process
	A substitution unifies two values if when applied to both it results in equal results

$S=\{r\mapsto y,s\mapsto y, d\mapsto s\}$
$a=\text{red},b=\text{yes}$
$S(\text{red})\neq S(\text{yes})$ -> S is a not a unifying substitution

---
$a=3,b=y$
$S=\{y\mapsto 3\}$
$S(a)=S(b)=3$ -> S is a unifying substitution

---
 $a=3*7$
 $b=3+z$
 There is no unifying substitution as they are of different structure.

---
$a=1+z$
$b=z$
$S=\{z\mapsto 1+1+1+\cdots\}$
$S(a)=S(b)=1+1+1+\cdots$

## Algorithm Signature
$S=\text{unify}(a,b)$
$S(a)=S(b)$
A unifying S may not exist at all, or may not be finite.

# Applying Unification to Type Systems

$a=\text{Int}\mapsto \alpha$
$b=\beta\mapsto \text{Bool}$
$S=\{\alpha\mapsto\text{Bool},\beta\mapsto\text{Int}\}$
$S(a)=S(b)=\text{Int}\mapsto\text{Bool}$
---
$a=\text{List} \;\alpha$
$b=\beta\mapsto\text{Bool}$
No unifying substitution exists

---
$a=\alpha\mapsto \text{Int}$
$b=\alpha$
$S=\{\alpha\mapsto\text{Int}\rightarrow\text{Int}\rightarrow\cdots\rightarrow\text{Int}\}$
$S(a)=S(b)=\text{Int}\rightarrow\cdots\rightarrow\text{Int}\rightarrow\text{Int}$

	Unification can 'merge' types while preserving all type constrainsts

# Unification Algorithm for Hindley-Milner Types
## The Algorithm
unify(a: MonoType, b: MonoType) -> Substitution:
	if a is a type variable:
		if b is the same type variable:
			return {}
		if b contains a:
			throw ==error== "occurs check failed, cannot create infinite type"
		returns {$a\mapsto b$}
	if b is a type variable:
		return unify(b,a)
	if a and b are both type function applications:
		if a and b have different type functions:
			throw ==error== "failed to unify, different type functions"
		let S = {}
		for i in range(number of type function arguments):
			S = combine(S,unify(S(a.arguments[i]),S(b.arguments[i])))
		return S

```Typescript
function unify(a: MonoType, b: MonoType): Substitution {
    if (a instanceof TypeVar) {
        if (b instanceof TypeVar && a.name == b.name)
            return {};
        if (contains(b, a))
            throw new TypeInferenceError('occurs check failed,' +
                ' cannot create infinite type');
        return { [a.name]: b }
    }

    if (b instanceof TypeVar)
        return unify(b, a);

    if (a instanceof TypeFuncApp && b instanceof TypeFuncApp) {
        if (a.constructorName !== b.constructorName)
            throw new TypeInferenceError('failed to unify,' +
                ' different type functions');
        let S: Substitution = {};
        for (let i = 0; i < a.args.length; i++) {
            S = combine(S, unify(apply(S, a.args[i]), apply(S, b.args[i])));
        }
        return S;
    }
}
```

# Type Order and the $\sqsubseteq$ Relation in Hindley-Milner

| More General                                               |
| ---------------------------------------------------------- |
| $\forall \alpha. \;\forall\beta.\; \alpha\rightarrow\beta$ |
| $\forall\alpha.\;\alpha\rightarrow\text{Bool}$             |
| $\text{Int}\rightarrow\text{Bool}$                         |
| Less General                                               |

Type on left is ==more general== than type on right
$\forall \alpha. \;\forall\beta.\; \alpha\rightarrow\beta.  \sqsubseteq \text{Int}\rightarrow\text{Bool}$

## Syntax for Type Order
$\sigma\sqsubseteq\sigma$
$\forall\alpha.\;\alpha\sqsubset\text{Int}$

## Formal Definition
$\sigma_1$ is more general than $\sigma_2$ if there is a substitution $S$ that maps the for-all quantified variables in $\sigma_1$, and $S(\sigma_1) = \sigma_2$

# Instantiation in Type Systems and Hindley-Milner
	find typs that are less generals
	
$\forall\alpha.\;\forall\beta.\;\alpha\rightarrow\beta$ => $\text{Int}\rightarrow\text{List}\;\gamma$
with
$S=\{\beta\mapsto\text{List}\;\gamma,\alpha\mapsto\text{Int}\}$

If $\sigma_1 \sqsubseteq \sigma_2$, an expression of type $\sigma_2$ can be used where one of type $\sigma_1$ is needed.

# Generalisation of Types in Hindley-Milner
	Add for all quantifier into a free type variable in a type

$$\forall\beta.\;\alpha\rightarrow\beta$$
$$\downarrow$$
$$FV(\forall\beta.\;\alpha\rightarrow\beta)=\alpha$$
$$\downarrow$$
$$\forall\alpha.\;\forall\beta.\;\alpha\rightarrow\beta$$

Can only generalise a type when the type variable is not free in the context

generalise$(\Gamma,\sigma)$ returns the most generalised version of the type $\sigma$
## Example


$\begin{align*} \Gamma &= \begin{array}{l} x : \beta, \\ y : \text{List } \gamma \to \text{Int}, \\ z : \forall\delta. \delta \end{array} & \begin{array}{l} FV(\Gamma) = \{ \beta, \gamma \} \\ FV(\sigma) = \{ \alpha, \beta, \gamma, \delta \} \\ FV(\sigma) - FV(\Gamma) = \{ \alpha, \delta \} \end{array} \\[2ex] \sigma &= \forall\varepsilon. \alpha \to \beta \to \gamma \to \delta \to \varepsilon \\[2ex] \text{generalise}(&\Gamma, \sigma) = \forall\alpha. \forall\delta. \forall\varepsilon. \alpha \to \beta \to \gamma \to \delta \to \varepsilon \end{align*}$

# Intro to Hindley-Milner Typing Rules
## Variable Typing Rule
$$\frac{x : \sigma \in \Gamma}{\Gamma \vdash x : \sigma}$$
1) If "the variable '$x$' has type of polytype '$\sigma$'" is in context $\Gamma$
2) then from the context '$\Gamma$' it follows that "the variable '$x$' has type of polytype '$\sigma$'"


$\Gamma=$
$\;\;\text{age}:\text{Int},$
$\;\;\text{odd}:\text{Int}\rightarrow\text{Bool}$

Q: what is the type of age given the context of '$\Gamma$'?
$\Gamma\vdash\text{age}:???$
$x=\text{age},\sigma=\text{Int}$
$$\frac{\text{age}:\text{Int}\in\Gamma}{\Gamma\vdash\text{age}:\text{Int}}$$
A: Int
## Application Typing Rule
$$\frac{\text{premise}}{\text{conclusion}}$$
$$\frac{\Gamma\vdash e_0:\tau_a \rightarrow\tau_b\;\;\;\;\Gamma\vdash e_1:\tau_a}{\Gamma\vdash e_0\;e_1:\tau_b}$$
1) If $e_0$ is of ==type== $\tau_a\rightarrow\tau_b$ and $e_1$ is of ==type== $\tau_a$
2) $e_0$ applied to $e_1$ is ==type== $\tau_b$

1) If premise
2) Then conclusion

$\Gamma=$
	$\text{age}:\text{Int},$
	$\text{odd}:\text{Int}\rightarrow\text{Bool}$
$\Gamma\vdash \text{odd age}:\text{Bool}$ <- inference

$$\frac{\frac{\text{odd}:\text{Int}\rightarrow\text{Bool}\in\Gamma}{\Gamma\vdash\text{odd}:\text{Int}\rightarrow\text{Bool}}\text{[var]}\;\;\frac{\text{age}:\text{Int}\in\Gamma}{\Gamma\vdash\text{age}:\text{Int}}\text{[var]}}{\Gamma\vdash\text{odd age}:\text{Bool}}\text{[app]}$$

Conclusion $[\text{rule}]$ (premise)
1. $\Gamma \vdash \text{odd} : \text{Int} \rightarrow \text{Bool} \;[\text{var}] \;(\text{odd} : \text{Int} \rightarrow \text{Bool} \in \Gamma)$
2. $\Gamma \vdash \text{age} : \text{Int} \;[\text{var}] \;(\text{age} : \text{Int} \in \Gamma)$
3. $\Gamma \vdash \text{odd age} : \text{Bool} \;[\text{app}] \;(1, 2)$

## Unifying Constraints with Typing Rules
$$\begin{array}{c}
\dfrac{
  \dfrac{\text{odd} : t4 \in \Gamma}{\Gamma \vdash \text{odd} : t1 \to t2} \quad
  \dfrac{\text{age} : t5 \in \Gamma}{\Gamma \vdash \text{age} : t3}
}
{\Gamma \vdash \text{odd age} : t0}
\end{array}$$
t0 ~ t2
t1 ~ t3
t1 -> t2 ~ t4
t4 ~ Int -> Bool
t3 ~ t5
t5 ~ Int

## Finding Type Errors with Typing Rules
$$\begin{array}{c}
\dfrac{
  \dfrac{\text{odd} : t4 \in \Gamma}{\Gamma \vdash \text{odd} : t1 \to t2} \quad
  \dfrac{\text{hungry} : t5 \in \Gamma}{\Gamma \vdash \text{hungry} : t3}
}
{\Gamma \vdash \text{odd hungry} : t0}
\end{array}$$
t0 ~ t2
t1 ~ t3
t1 -> t2 ~ t4
t4 ~ Int -> Bool
t3 ~ t5
t5 ~ Bool

----
$\Gamma\vdash\text{odd hungry}: t0$
1) $\text{unify}(t0,t2)=\{t0)\mapsto t2\}$
	$\Gamma\vdash\text{odd hungry}: t2$
2) $\text{unify}(t1,t3)=\{t1)\mapsto t3\}$
	t3 -> t2 ~ t4
	t4 ~ Int -> Bool
	t3 ~ t5
	t5 ~ Bool
3) $\text{unify}(t3\rightarrow t2,t4)=\{t4)\mapsto t3\rightarrow t2\}$
	t3 -> t2 ~ Int -> Bool
4) $\text{unify}(t3\rightarrow t2,\text{Int}\rightarrow\text{Bool})=\{t3\mapsto\text{Int},t2\mapsto\text{Bool}\}$
	$\Gamma\vdash\text{odd hungry}: \text{Bool}$
	Int ~ t5
	t5 ~ Bool
5)$\text{unify}(\text{Int},t5)=\{t5\mapsto\text{Int}\}$
	Int ~ Bool  => Type Error

## Function Abstraction Typing Rule
$$\dfrac{\Gamma, x : \tau_a \vdash e : \tau_b}{\Gamma \vdash \textbackslash x \to e : \tau_a \to \tau_b}$$
$$\frac{\text{premise}}{\text{conclusion}}$$
==If== from the context '$\Gamma$' plus the assignment "variable 'x' has type '$\tau_a$'" if follows that expression 'e' has type '$\tau_b$'

==then== from the context '$\Gamma$' it follows that the expression '$\textbackslash x \rightarrow e$' has type '$\tau_a\rightarrow\tau_b$'

The function parameters get replaced by the types

$\Gamma=$
$\;\;\;\text{gt: Int}\rightarrow\text{(Int}\rightarrow\text{Bool)}$

### Q: What is the type of '$\textbackslash n \rightarrow \text{gt 3 n}$ given the context '$\Gamma$' ?
$x=n$
$\text{e = gt 3 n}$
$\tau_a=\text{Int}$
$\tau_b = \text{Bool}$

$$\Gamma \vdash \textbackslash n \rightarrow \text{gt 3 n: ???}$$

$$
\frac{\Gamma, n : \text{Int} \vdash \text{gt}\ 3\ n : \text{Bool}}
     {\Gamma \vdash \textbackslash n \rightarrow \text{gt}\ 3\ n : \text{Int} \rightarrow \text{Bool}}
$$
#### Reading the Rule
The whole rule is saying:

1. **Premise**: If, in a context where `n` has type `Int`, the expression `\text{gt}\ 3\ n` has type `Bool`...
2. **Conclusion**: ...then the function `\n \rightarrow \text{gt}\ 3\ n` has the type `\text{Int} \rightarrow \text{Bool}`, i.e., it is a function that takes an integer and returns a boolean.

$$
\textbf{Practical Example:}
$$

$$
\Gamma = \text{gt} : \text{Int} \rightarrow (\text{Int} \rightarrow \text{Bool})
$$

$$
\begin{array}{rl}
1. & \Gamma, n : \text{Int} \vdash n : \text{Int} \quad [\text{var}] \ (n : \text{Int} \in \Gamma, n : \text{Int}) \\
2. & \Gamma, n : \text{Int} \vdash \text{gt} : \text{Int} \rightarrow (\text{Int} \rightarrow \text{Bool}) \quad [\text{var}] \ (\text{gt} : \text{Int} \rightarrow (\text{Int} \rightarrow \text{Bool}) \in \Gamma, n : \text{Int}) \\
3. & \vdash 3 : \text{Int} \quad [\text{literal}] \\
4. & \Gamma, n : \text{Int} \vdash \text{gt}\ 3 : \text{Int} \rightarrow \text{Bool} \quad [\text{app}] \ (2, 3) \\
5. & \Gamma, n : \text{Int} \vdash \text{gt}\ 3\ n : \text{Bool} \quad [\text{app}] \ (1, 4) \\
6. & \Gamma \vdash \textbackslash n \rightarrow \text{gt}\ 3\ n : \text{Int} \rightarrow \text{Bool} \quad [\text{abs}] \ (5) \\
\end{array}
$$
## Let Typing Rule
$$
\frac{
    \Gamma \vdash e_0 : \sigma \quad \Gamma, x : \sigma \vdash e_1 : \tau
}{
    \Gamma \vdash \text{let}\ x = e_0\ \text{in}\ e_1 : \tau
}
$$
If we bind an expression $e_0$ to a variable x with type $\sigma$ and doing so results in the let body $e_1$ having type $\tau$

then the let statement as a whole has type $\tau$

$\Gamma$ =
    gt : Int → (Int → Bool)

$\Gamma \vdash$ let a = 2 in gt 3 a : Bool

$e_0$ = 2
$e_1$ = gt 3 a
x = a
$\sigma$ = Int
$\tau$ = Bool

$$\frac{\Gamma \vdash 2 : \text{Int} \;\;\;\;\;\Gamma, \text{a} : \text{Int} \vdash \text{gt 3 a} : \text{Bool}}{\Gamma \vdash \text{let a = 2 in gt 3 a : Bool}}$$
## Instantiation Typing Rule
If $\sigma_1 \sqsubseteq \sigma_2$, an expression of type $\sigma_2$ can be used where one of type $\sigma_1$ is needed.

$$\frac{\Gamma \vdash e : \sigma_a \quad \sigma_a \sqsubseteq \sigma_b}{\Gamma \vdash e : \sigma_b}$$
If from $\Gamma$ it follows that $e$ has type $\sigma_a$ and $\sigma_a$ is more general than $\sigma_b$, then from the context it follows that $e$ has type $\sigma_b$

$\Gamma=$
reverse: $\forall\alpha.$ $\text{List} \; \alpha\rightarrow\text{List} \;\alpha,$
ages: $\text{List Int}$

What is the type of 'reverse ages' given the context ?
$\Gamma \vdash \text{reverse ages}:\text{List Int}$


## Generalization Typing Rule
$$\frac{\Gamma \vdash e : \sigma \quad \alpha \notin FV(\Gamma)}{\Gamma \vdash e : \forall \alpha. \sigma}$$

If e has type $\sigma$ and type variable $\alpha$ is not free in the context

then for-all quantify e's type $\sigma$ with variable $\alpha$
