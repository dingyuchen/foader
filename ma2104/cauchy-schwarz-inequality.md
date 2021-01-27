# Cauchy-Schwarz Inequality

For any $\vec u, \vec v \in \R^n$,

$$
\begin{aligned}
  \vec u \cdot \vec v &\leq |\vec u||\vec v| \\
  \text{i.e. } (\vec{u} \cdot \vec v)^2 &\leq (\vec u \cdot \vec u) (\vec v \cdot \vec v)
\end{aligned}
$$

## Proof

If $\vec u = \vec 0 \in \R^n$, then LHS = 0 = RHS.

Assume $\vec u \neq \vec 0$. Consider the quadratic polynomial

$$
\begin{aligned}
  &(\vec u \cdot \vec u)x^2 + 2(\vec u \cdot \vec v)x + (\vec{v} \cdot \vec{v}) \\
  &= (\sum^n_{i = 1} {u_i}^2) x^2 + (2 \sum^n_{i = 1} {u_i} v_i) x + (\sum^n_{i = 1} {v_i}^2) \\
  &= \sum^n_{i = 1} (u_i x + v_i)^2 \\
  & \Rightarrow \text{discriminant of polynomial is } \leq 0 \\
  &\therefore 4(\vec u \cdot \vec v)^2 - 4(\vec u \cdot \vec{u})(\vec{v} \cdot \vec{v}) \leq 0 \\
  &\therefore (\vec{u} \cdot \vec v)^2 \leq (\vec u \cdot \vec u) (\vec v \cdot \vec v)
\end{aligned}
$$