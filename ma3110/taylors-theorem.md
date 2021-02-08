# Taylor's Theorem

Let $f$ be a function such that $f \in C^n([a, b])$ and $f^{( n + 1 )}$ exists on $(a, b)$.

If $x_0 \in [a, b]$, then for any $x \in [a, b]$, there exists a point $c$ between $x$ and $x_0$ such that

$$f(x) = f(x_0) + f'(x_0)(x - x_0) + \frac{f''(x_0)}{2!}(x - x_0)^2 + ... + \frac{ f^{(n)}(x_0) }{n!}(x - x_0)^n + \frac{f^{(n + 1)}(c)}{(n+1)!}(x - x_0)^{n + 1} $$

> We can express the function as a polynomial + some error

## Proof

Fix $x \in [a, b]$. We may assume that $x_0 \neq x$. 

Let $M$ be the unique number such that

$$f(x) = f(x_0) + f'(x_0)(x - x_0) + \frac{f''(x_0)}{2!}(x - x_0)^2 + ... + \frac{ f^{(n)}(x_0) }{n!}(x - x_0)^n + M(x - x_0)^{n + 1} $$

Define $F:[a, b] \rightarrow \R$

$$F(t) = F(t) + F'(t)(x - t) + \frac{F''(t)}{2!}(x - t)^2 + ... + \frac{ F^{(n)}(t) }{n!}(x - t)^n + M(x - t)^{n + 1} $$

Then $F$ is continuous on $[a, b]$ and differentiable on $(a, b)$.

$$F(x) = f(x)$$
$$F(x_0) = f(x)$$
$$\therefore F(x) = F(x_0)$$

So by [[rolles-theorem]], there exists a $c$ between $x$ and $x_0$ such that $F'(c) = 0$.

$$F'(t) = \frac{f^{(n + 1)}(t)}{n!}(x - t)^n + M(n + 1)(x - t)^n (-1)$$


$$\therefore F'(c) = \frac{f^{(n + 1)}(c)}{n!}(x - c)^n - M(n + 1)(x - c)^n = 0$$

$$\therefore M = \frac{f^{(n + 1)}(c)}{(n + 1)!}$$

[//begin]: # "Autogenerated link references for markdown compatibility"
[rolles-theorem]: rolles-theorem "Rolle's Theorem"
[//end]: # "Autogenerated link references"