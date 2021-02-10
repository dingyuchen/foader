# Geometry of Linear Programming

## Polyhedron

A **polyhedron** or **polyhedral set** is a set of the form $\{\bold x \in \R^n \vert \bold{Ax} \leq \bold b \}$, where $\bold A \in \R^{m \times n}$ and $\bold b \in \R^m$

Geometrically, ia polyhedron is a finite intersection of half spaces.

The feasible region for a standard form LP $\{\bold x \in \R^n \vert \bold{Ax} = \bold b, \bold x \geq 0 \}$ is a polyhedron.

----------

We characterize the corner points of polyhedron
- geometrically
- algebraically

The main result states that for a nonempty polyhedron $P$ 
- $P$ has at least one corner point iff it does not contain a line.
- If $P$ has a corner point, the search for optimal solutions to LPs can be restricted to finding corner points.

## Corner Point

Consider a convex set $P \subset \R^n$.

A point $\bold x^* \in P$ is an **extreme point** of $P$ if whenever points $\bold{y, z} \in P$ and scalar $\lambda \in (0, 1)$ are such that $\bold x^* = \lambda \bold y + (1 - \lambda) \bold z$, we have $\bold y = \bold z = \bold x^*$.

> If we try to extend a line passing $\bold x^*$, the endpoints will be outside of the convex set.

A point $\bold x^* \in P$ is a **vertex** of $P$ if there is a $c \in P$ such that $\bold c^T \bold x^* > \bold c^T \bold y$ for all $\bold y \in P \backslash \{\bold x^*\}$.

## Terminology

Consider $\bold x^* \in \R^n$ and the constraint $\bold a_i^T \bold x^* \gtreqqless b_i$.

If $\bold a_i^T \bold x^* = b_i$, we say this constraint is **active/binding/tight** at $\bold x^*$.

Constraints $\bold a_i^T \bold x^* \geq b_i, i \in I$ are said to be **linearly independent** if the corresponding vectors $\bold a_i, i \in I$ are linearly independent.

$\bold x^* \in \R^n$ is a **basic feasible solution** (BFS) of a polyhedron $P$ if $\bold x^* \in P$ and $n$ linearly independent constraints are active at $\bold x^*$.