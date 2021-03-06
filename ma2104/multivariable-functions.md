# Multivariable Functions

Multivariable Functions

An "$n$-dimensional" vector-valued function of "$m$-variables" is a function of the form $f: R \rightarrow \R^n$ where
$R \subseteq \R^m$ is a (open) region.

Take the function to take in a $m$-dimensional vector as input and returns a $n$-dimensional vector.

## Limits

$\epsilon - \delta$ defintion for multivariable functions.

Let $t_o \in I$ and $\vec L \in \R^n$. Say $\vec r$ has limit $\vec L$ as $t \rightarrow t_0$ iff 

$$\forall \epsilon \in \R_{>0}, \exist \delta \in \R_{>0}$$

### Limit Laws

1. [[todo]]

## Continuity

A function $f$ is **continuous at the point $\bold x_0$** if 

1. $f$ is defined at $\bold x_0$.
2. $\lim_{\bold x \rightarrow \bold x_0} f(\bold x)$ exists
3. $\lim_{\bold x \rightarrow \bold x_0} f(\bold x) = f(\bold x_0)$.

A function is **continuous** if it is continuous at every point in its domain.

### Continuity of Compositions

Suppose $f: S \rightarrow \R^m, S \subseteq \R^l$
and $g: R \rightarrow \R^n, S \subseteq \R^m$
and $f(S) \subseteq R$ (so that $g \circ f : S \rightarrow \R^n$ is defined)

For any $\vec q_0 \in S$, if $f$ is continuous at $\vec q_0$
and $g$ is continuous at $f(\vec q_0)$
then $g \circ f$ is continuous at $\vec q_0$.

### Proof

[[todo]]

## Differentiability

There must exist some linear transformation $A$ such that 

Say $f$ is differentiable at $\vec p_0 \in R$ iff 
there exists a linear transformation $A : \R^m \rightarrow \R^n$
such that $\forall \epsilon \in \R_{> 0}, \exist \delta \in \R_{>0}$ such that

$$\vert f(\vec p) - (f(\vec p_0) + A \cdot (\vec p - \vec p_0)) \vert \leq \epsilon \vert \vec p - \vec p_0 \vert$$

The linear transformation $A$ is the uniquely determined (if it exists) and is called the (total) derivative of $f$ at $p_0$.

> uses hypothesis that $R$ is open.

- Say $f$ is continuously differentiable on $R$ iff $f$ is differentiable on $R$ and $f'$ is differentiable.

## Differentiability Implies Continuity

Suppose $f: R \rightarrow \R^n$ is differentiable at $\vec p_0 \in R$, then 
$f$ is continuous.

## Directional Derivative

The **derivative of $f$ at point $p_0$ in the direction of the vector $\vec u$**.

Let $R \subseteq \R^m$ be an open region.

Let $f : R \rightarrow \R^n$ be a function.

Let $\vec u \in \R^m$ be any vector("direction").

The _derivative of $f$ in the direction $\vec u$ at $\vec p_0 \in R$_ is the limit 
$(D_{\vec u} f)(\vec p_0) \in \R^n$ given by

$$(D_{\vec u} f)(\vec p_0) := \lim_{s \rightarrow 0} \frac{f( \vec p_0 + s \vec u ) - f(\vec p_0)}{s}$$

> Consider a (small) open interval $I = (-c, c) \subseteq \R$ such that $\forall s \in I$, one has $\vec p_0 + s \cdot \vec u \in R$.
>
> to get function $f_{\vec u, \vec p_0} : I \rightarrow \R^n, f_{\vec u, \vec p_0} := f(\vec p_0 + s \cdot \vec u)$
>
> Then $(D_{\vec u} f)(\vec p_0) = (\frac{d}{ds} f_{\vec u, \vec p_0})(0)$.

## Partial Derivatives

The partial derivatives are the directional derivatives of $f$ at $p_0$ in the basis vector directions.

In general:

Let $R \subseteq \R^m$ be an open region.

Let $f : R \rightarrow \R^n$ be a function.

Let $\vec e_1, ... \vec e_m \in \R^m$ be the standard basis vectors.

For $j \in \{ 1, ..., m \}$, the $j^{th}$ partial derivative of $f$ at $p_0 \in R$ is the derivative of $f$ in the direction $\vec e_j$ at $\vec p_0 \in R$
denoted as $\frac{\partial f}{\partial x_j}(\vec p_0)$ or $f_{x_j}(\vec p_0)$.

Thus 

$$ \frac{\partial f}{\partial x_j}(\vec p_0) = f_{x_j}(\vec p_0) = (D_{\vec e_j}f)(\vec p_0) $$

is the limit

$$\lim_{s \rightarrow 0} \frac{f( \vec p_0 + s \vec e_j ) - f(\vec p_0)}{s}$$

in $\R^n$ (if it exists).

## Relationship between Derivatives

Suppose $f: R \rightarrow \R^n$ is _differentiable at $\vec p_0 \in R$_ (so the total derivative exists and is a linear transformation $\R^m \rightarrow \R^n$)

Then for any $\vec u \in \R^n$, the $\vec u$-directional derivative $(D_{\vec u} f)(\vec p_0)$ of $f$ at $\vec p_0$ exists and is equal to 

$$(D_{\vec u} f)(\vec p_0) = (Df)(\vec p_0) \times \vec u \in \R^n$$

In particular, for each $j \in \{1, ..., m\}$,
the $j^{th}$ partial derivative $\frac{\partial f}{\partial x_j} (\vec p_0)$ of $f$ at $\vec p_0$ exists and is equal to 

$$\frac{\partial f}{\partial x_j}(\vec p_0) = (Df)(\vec p_0) \times \vec e_j \in \R^n$$

which is the $j^{th}$ column of the total derivative.

> It can happen that all partial derivatives exist but the function is not continuous at $\vec p_0$, hence not differentiable.

[//begin]: # "Autogenerated link references for markdown compatibility"
[todo]: ../todo "Todo"
[//end]: # "Autogenerated link references"