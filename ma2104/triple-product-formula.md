# Triple Product Formula

For any $\vec u, \vec v, \vec w \in \R^3$,

$$ (\vec u \times \vec v \cdot \vec w) = \begin{vmatrix}
  u_1 & u_2 & u_3 \\
  v_1 & v_2 & v_3 \\
  w_1 & w_2 & w_3 
\end{vmatrix} \in \R$$

## Proof

$$
\begin{aligned}
  (\vec u \times \vec v \cdot \vec w) &= 
  (\begin{vmatrix}
  u_2 & u_3 \\
  v_2 & v_3 
\end{vmatrix} \vec i - 
  \begin{vmatrix}
  u_1 & u_3 \\
  v_1 & v_3 
\end{vmatrix} \vec j +
  \begin{vmatrix}
  u_1 & u_2 \\
  v_1 & v_2 
\end{vmatrix} \vec k) \\
  &= (w_1 \begin{vmatrix}
  u_2 & u_3 \\
  v_2 & v_3 
\end{vmatrix} - 
  w_2 \begin{vmatrix}
  u_1 & u_3 \\
  v_1 & v_3 
\end{vmatrix} +
  w_3 \begin{vmatrix}
  u_1 & u_2 \\
  v_1 & v_2 
\end{vmatrix} ) \\
  &= \begin{vmatrix}
  u_1 & u_2 & u_3 \\
  v_1 & v_2 & v_3 \\
  w_1 & w_2 & w_3 
\end{vmatrix}
 
\end{aligned}
$$

> Expansion of $3 \times 3$ determinant along the 3rd row.
