# Interior Extremum Theorem

Suppose that $c$ is an interior point of an interval $I$ and $f : I \rightarrow \real$ is differentiable at $c$.
If $f$ has a relative extremum at $c$, then $f'(c) = 0$.

> The converse is not true. Eg. inflection points.

## Proof
Suppose $f$ has a relative maximum at $c$.
1. If $f'(c) > 0$, there exists $\delta > 0$ such that $(c - \delta, c + \delta) \subseteq I$, $f(x) < f(c)$ for every $x \in (c - \delta, c)$ and $f(x) > f(c)$ for every $x \in (c, c + \delta)$. This contradicts teh assumption that $f$ has a relative maximum at $c$.
2. If $f'(c) < 0$, then likewise we get a contradiction.

Hence $f'(c) = 0$.

The case of a relative minimum at $c$ is similar.