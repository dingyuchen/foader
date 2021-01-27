# Cauchy Mean Value Theorem

Let $f$ and $g$ be continuous on $[a, b]$ and differentiable on $(a, b)$, and assume that $g'(x) \neq 0$ for all $x \in (a, b)$.

Then there exists $c \in (a, b)$ such that

$$ \frac{f(b) - f(a)}{g(b) - g(a)} = \frac{f'(c)}{g'(c)}$$

> We cannot have $g'(x) = 0$ in the denominator, therefore condition must hold that $g'(c) \neq 0$ and $c \in (a, b)$ 
> so that our result is not undefined.

## Proof

First we claim that $g(a) \neq g(b)$.

Otherwise, by [[rolles-theorem]], there will be some $x_0$ such that $g'(x_0) = 0$, 
contradicting our assumption.

Rewriting, we get

$$ \frac{f(b) - f(a)}{g(b) - g(a)} g'(x) - f'(x) $$

which we can massage into a derivative of some function $h$.

Define $h:[a, b] \rightarrow \R$ by

$$ h(x) := \frac{f(b) - f(a)}{g(b) - g(a)}(g(x) - g(a)) - (f(x) - f(a)) $$

