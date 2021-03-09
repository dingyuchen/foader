# Multivariable Integration

## Integral of a Function

For any compact rectangle $X$ in Euclidean space, we will 
- specify a vector space $R(X)$ of $\R$-valued functions on $X$.
- define a linear map $R(X) \rightarrow \R$, $f \rightarrow \int_X f(x) \; dx$.

A compact rectangle in $\R^m$ is a subset $X \subseteq \R^m$ of the form $X = X_1 \times X_2 \times ... X_m$
where each $X_i$ is a closed and bounded interval in $\R$.

The volume of $X$ is $\vert X \vert := \prod^m_{i = 1} (b_i - a_i) \in \R_{\geq 0}$

A partition of $X_i$ is a collection of closed sub-intervals of $X_i$ of the form $P_i = \{[x_0, x_1], ..., [x_{k - 1}, x_k] \}$

A partition of $X$ is a collection of subsets of $X$ of the form $P_i = \{R_1 \times ... \times R_m \subseteq X : R_1 \in P_1, ..\}$

The **norm** of $P$ is $\Vert P \Vert = \max_i (\max_{R_i \in P_i} \vert R_i \vert)$
i.e. the maximum side length among the pieces in $P$.

## Riemann Sum

Let $X \subseteq \R^m$ be a compact rectangle, 
let $f: X \rightarrow \R^n$ be a vector valued function on $X$.

For any partition $P$ of $X$,
for any function $t: P \rightarrow X$ such that $\forall R \in P$, $t(R) \in R$.

> choose a point in that partition

the Riemann Sum of $f$  with respect to $P$ and $t$ is

$$S(f; P, t) := \sum_{R \in P} f(t(R)) \cdot \vert R \vert \; \in \R^n$$

## Riemann Integrable

We say that the function $f: X \rightarrow \R^n$ is Riemann integrable iff 
the limit $\lim_{P, t, \Vert P \Vert \rightarrow 0} S(f; P, t)$ exists in $\R^n$.

$\exist L \in \R^n$ such that $\forall \epsilon \in \R_{\geq 0}$, $\exist \delta > 0$ such that 

$\forall$ partition $P$ of $X$ with $\Vert P \Vert < \delta$

$\forall$ function $t: P \rightarrow X$ with $\forall R \in P$, $t(R) \in R$,

one has $\vert S(f; P, t)- L \vert < \epsilon$

When this holds, the vector $L \in \R^n$ is uniquely determined by $f$ and is denoted $\int_X f(x) \; dx$ called the Riemann integral of $f$ over $X$.

## Properties of Riemann Integrals

1. Constant multiple
2. Linear over sum and difference
3. Domination ($\int$ is order-preserving)
4. Additivity: Sum of non overlapping regions

## Theorem

> non trivial!

Every continuous function on $X$ (compact rectangle) is Riemann integrable.

More generally,

A function $f:X \rightarrow \R$ is Riemann integrable iff $f$ is bounded and $Dis(f) := \{ x \in X : \text{f is not continuous on X}\}$
is of measure $0$ in $\R^m$.

This means $\forall \epsilon \in \R_{> 0}$, $\exist$ rectangles $R_1, R_2, ..., R_n \in \R^m$ such that $Dis(f) \subseteq R_1 \cup, ..., \cup R_n$ and $\vert R_1 \vert + ... < \epsilon$

> The discontinuous points are small enough that they don't affect volume.

## Fubini Theorem for Riemann Integral

Let $X \subseteq \R^m$ and $Y \in \R^l$ be compact rectangles

Let $f: X \times Y \rightarrow \R$ be a Riemann integrable function.

If the function $F: X \rightarrow \R$, $F(x) = \int_Y f(x, y) \; dy$ is defined.

then $F$ is Riemann integrable over $X$, and 

$$\int_{X \times Y} f(x,y) \; d(x, y) = \int_X F(x) \; dy = \int_X \int_Y f(x, y) \; dy \; dx$$

> This allows us to reduce integration in $m$ variables to iterated integration in 1 variable

### Consequence

If $f: X \times Y \rightarrow \R$ is continuous on $X \times Y$.
Then

$$\int_Y \int_X f(x, y) \; dx \; dy = \int_{X \times Y} f(x,y) \; d(x, y) = \int_X \int_Y f(x, y) \; dy \; dx$$


