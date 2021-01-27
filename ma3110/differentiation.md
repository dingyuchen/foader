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

Let $I$ be an interval, $f : I \rightarrow \R$ and $x_0 \in I$.

1. We say that $f(x_0)$ is the **absolute maximum** of $f$ on $I$ if $f(x_0) \geq f(x)$ for all $x \in I$.
2. We say that $f(x_0)$ is the **relative maximum** of $f$ on $I$ if there exists $\delta > 0$ such that for all $x \in (x_0 - \delta, x_0 + \delta) \subseteq I$, $f(x_0) \geq f(x)$.

> There can be no absolute maximum, eg. $f(x) = \frac{1}{x}$ on $(0, 1)$, however, [[extreme-value-theorem]] states that there definitely exists an absolute maximum in **closed** interval.

**Absolute minimum** and **relative minimum** is defined similarly.

- We say $f(x_0)$ is a **relative extremum** of $f$ if $f(x_0)$ is either a relative maximum or minimum.

> A relative extremum can only occur at an [[interior-point]], but an absolute extremum can occur at the end points of the interval.
>
> So if a function has an absolute maximum point at $x_0$, it is not guaranteed to also have a relative maximum at $x_0$.

### Lemma 6.3.1

[[ma3110-lemma-631]]

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

[[todo]]
#### Remark

Are the converse of 1 and 2 in [Theorem 6.3.3](#theorem-633) true?

> Yes.

### First Derivative Test

[[first-derivative-test]]

> Converse is [[interior-extremum-theorem]]
> > which implies [[rolles-theorem]]

## Key Theorems

- [[interior-extremum-theorem]]
- [[rolles-theorem]]
- [[mean-value-theorem]]
- [[cauchy-mean-value-theorem]]
- Taylor's Theorem

## Next
- [[higher-derivatives]]


[//begin]: # "Autogenerated link references for markdown compatibility"
[inverse-function-theorem]: inverse-function-theorem "Inverse Function Theorem"
[extreme-value-theorem]: extreme-value-theorem "Extreme Value Theorem"
[interior-point]: interior-point "Interior Point"
[ma3110-lemma-631]: ma3110-lemma-631 "MA3110 Lemma 6.3.1"
[mean-value-theorem]: mean-value-theorem "Mean Value Theorem"
[todo]: ../todo "Todo"
[first-derivative-test]: first-derivative-test "First Derivative Test"
[interior-extremum-theorem]: interior-extremum-theorem "Interior Extremum Theorem"
[rolles-theorem]: rolles-theorem "Rolle's Theorem"
[cauchy-mean-value-theorem]: cauchy-mean-value-theorem "Cauchy Mean Value Theorem"
[higher-derivatives]: higher-derivatives "Higher Derivatives"
[//end]: # "Autogenerated link references"