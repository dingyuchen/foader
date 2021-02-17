# Linear Mappings

Let $V$ and $W$ be vector spaces.

A mapping $T : V \rightarrow W$ is called a **linear** mapping if it _preserves the vector structure_.
That is,

- $T(u + v) = T(u) + T(v) \; \forall u, v \in V$
- $T(au + v) = aT(u) + T(v) \; \forall a \in \mathcal{F}, \forall u \in V$

The set of linear mappings from $V$ to $W$ is denoted $\mathcal{L}(V, W)$.

> Not every element of $\mathcal{L}$ is a basis, because not all of them are bijections.

## Everything is a Vector

The vector space $\mathcal{L}(V, \mathcal{F})$ is called the **dual** space to the space $V$, denoted as $\hat V$.
So if $\alpha \in \hat V$, then for any $u \in V$, $\alpha(u)$ is just a number.

This means that vectors are linear transformations.

Define $aT$ where $a$ is a scalar and $T$ is a linear maping from $V$ to $W$ as

$$ (aT)u \equiv a(Tu) \; \forall u \in V$$

and since

$$ (T_1 + T_2)(u) = T_1(u) + T_2(u) \; \forall u \in V$$

So the set of linear transformations from $V$ to $W$ is a vector space.

### Zero Vector of Transformations

The mapping that takes every element of a vector space to its zero vector is an element of $\mathcal{L}(V, V)$, which is the zero vector in the vector space $\mathcal{L}(V, V)$.

## Kernel and Range

If $T \in \mathcal{L}(V, W)$, then the **kernel** of $T$, $\ker(T)$, is the set of elements in $V$ that are mapped to the zero vector in $W$.

- $\ker(T)$ is a subspace of $V$.

The dimension of $\ker(T)$ is traditionally called the **nullity** of $T$, $Null(T)$.

- $T$ is injective iff $\ker(T)$ consists of the zero vector only. ($Null(T) = 0$)
