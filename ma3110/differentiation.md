# Differentiation
#math

Chapter 6 of [Introduction to Real Analysis](https://sciencemathematicseducation.files.wordpress.com/2014/01/0471433314realanalysis4.pdf)

## Limits of functions
Roughly speaking, a function $f$ has a limit $L$ at the point $x = a$ if 
$$x \approx a \Rightarrow f(x) \approx L$$

## Chain Rule

$$(g \circ f)' (a) = g'(f(a))f'(a)$$

$$\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$$

The derivative of a composite function is the derivative of the outer function with respect to the inner function multiplied by derivative of the inner function w.r.t. $x$.

## Inverse Function Theorem
[[inverse-function-theorem]]

## Mean Value Theorem and Applications

### Definitions

Let $I$ be an interval, $f : I \rightarrow \real$ and $x_0 \in I$.

1. We say that $f(x_0)$ is the **absolute maximum** of $f$ on $I$ if $f(x_0) \geq f(x)$ for all $x \in I$.
2. We say that $f(x_0)$ is the **relative maximum** of $f$ on $I$ if there exists $\delta > 0$ such that for all $x \in (x_0 - \delta, x_0 + \delta) \subseteq I$, $f(x_0) \geq f(x)$.

> There can be no absolute maximum, eg. $f(x) = \frac{1}{x}$ on $(0, 1)$, however, [[extreme-value-theorem]] states that there definitely exists an absolute maximum in **closed** interval.

**Absolute minimum** and **relative minimum** is defined similarly.

- We say $f(x_0)$ is a **relative extremum** of $f$ if $f(x_0)$ is either a relative maximum or minimum.

> A relative extremum can only occur at an [[interior-point]], but an absolute extremum can occur at the end points of the interval.
>
> So if a function has an absolute maximum point at $x_0$, it is not guaranteed to also have a relative maximum at $x_0$.

### Lemma 6.3.1

Let $f: (a, b) \rightarrow \real$ and $f'(c)$ exists for some $c \in (a, b)$.

If $f'(c) > 0$ [[todo]]

#### Proof

### Theorem 6.3.2

If $f$ is continuous on $[a, b]$ and differentiable on $(a, b)$ and $f'(c) = 0 \forall c \in (a, b)$, then $f$ is constant on $[a, b]$.

#### Proof

If $a < x \leq b$, then by the [[mean-value-theorem]] there is a point $c \in (a, b)$ such that

$$f'(c) = \frac{f(x) - f(a)}{x - a}$$

However, we know that $f'(x) = 0$ for all $x \in (a, b)$ and thus $f'(c) = 0 \implies f(x) = f(a)$.

$\therefore f$ is constant.

### Theorem 6.3.3

Let $f$ be differentiable on $(a, b)$.
1. If $f'(x) \geq 0$ for all $x \in (a, b)$, then f is increasing on $(a, b)$.
2. If $f'(x) \leq 0$ for all $x \in (a, b)$, then f is decreasing on $(a, b)$.

#### Proof

#### Remark

Are the converse of 1 and 2 in [Theorem 6.3.3](#theorem-633) true?

> Yes.

### First Derivative Test

Let $f$ be continuous on $[a, b]$ and $c \in (a, b)$. 
Suppose that f is differentiable on $(a, b)$ except possibly at $c$.

1. If there is a neighborhood $(c - \delta, c + \delta) \subseteq I$ of $c$ such that $f'(x) \geq 0$ such that for $x \in (c - \delta, c)$ and $f'(x) \leq 0$ for $x \in (c, c + \delta)$, then 
$$ f(c) \geq f(x), \, \forall x \in (x - \delta, x + \delta)$$
Hence $f$ has a relative maximum at $c$.

2. vice versa for relative minimum.

### Key Notes

- [[interior-extremum-theorem]]
- [[rolles-theorem]]
- [[mean-value-theorem]]
- Cauchy's Mean Value Theorem
- Taylor's Theorem


[//begin]: # "Autogenerated link references for markdown compatibility"
[inverse-function-theorem]: inverse-function-theorem "Inverse Function Theorem"
[extreme-value-theorem]: extreme-value-theorem "Extreme Value Theorem"
[interior-point]: interior-point "Interior Point"
[todo]: ../todo "Todo"
[mean-value-theorem]: mean-value-theorem "Mean Value Theorem"
[interior-extremum-theorem]: interior-extremum-theorem "Interior Extremum Theorem"
[rolles-theorem]: rolles-theorem "Rolle's Theorem"
[//end]: # "Autogenerated link references"