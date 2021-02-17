# Vector Space

## Vector

The basic idea is that vectors are things that can be multiplied by numbers and added together.

A **vector space** is _any_ set of things that can be multiplied by numbers and added together.

Something in the form 

$$ a x + b y = c z$$

## Scalar

A scalar can be either real or complex. Scalars are elements of $\mathcal{F} = \R \cup \Complex$.

## Vector Space

Vector spaces are just sets that are given properties to make them resemble $\mathcal{F}^n$.

### Vector Space Isomorphisms

----------
Recall:

Let $S$ and $T$ be 2 sets. A mapping $F : S \rightarrow T$ is called a **surjection** if for any $t \in T$, there exists $s \in S$ such that $F(s) = t$.

A mapping is an **injection** if for all $s_1, s_2 \in S, F(s_1) = F(s_2)$ implies that $s_1 = s_2$.

A mapping is a **bijection** if it is both surjective and injective.

$F$ has an **inverse** iff it is a bijection.

----------
Let $U$ and $V$ be vector spaces.
A mapping $\Phi : U \rightarrow V$ is said to be a **vector space homomorphism** if $\forall u \in U, v \in U, a \in \mathcal{F}$.

$$ \Phi(u + v) = \Phi(u) + \Phi(v)$$

$$ \Phi(au) = a\Phi(u)$$

If there exits a vector space homomorphism from $U$ to $V$ which is a bijection,
then we call the homomorphism an **isomorphism**.

## Dimensions

A vector space is said to be **finite-dimensional over** $\mathcal{F}$ if it is isomorphic to $\mathcal{F}^n$ for some (finite) integer $n$.

> No finite-dimensional vector space can be isomorphic to $\mathcal{F}^n$ for two different values of $n$, so this number is a fixed property of the vector space, called the **dimension** of the vector space.

Vector spaces that aer not finite-dimensional are called **infinite-dimensional**.

## Span, Linear Independence, Basis

A **linear combination** of the elements of a list of vectors $v_i$ is just any vector of the form $a^1v_1 + a^2v_2 + ...$ where the $a^i$ are scalars.

The **span** of a list of vectors is defined to be the set of all linear combinations of vectors in the list.

> Example the space of the list $\{ \binom{1}{0}, \binom{0}{1} \}$ is all of $\mathcal{F}^2$.

A list of vectors $v_i \in V$ is said to be **linearly independent** if the equation $\sum a^iv_i = 0$ implies $a^i = 0$ for every $i$.

> Vectors in the span of a linearly independent vectors can be expressed as a _unique_ linear combination.

A **basis** of a vector space $V$ is any list of vectors in $V$ which _both_ spans $V$ and is linearly independent.

> Every finite-dimensional vector space has a basis.

> No vector space ever has just 1 basis.

----------

Suppose $U$ is a subspace of a finite-dimensional vector space $W$. Then $W$ has another subspace, $V$, such that $W = U \oplus V$

### Bases

We can express any vector $v$ in a finite-dimensional vector space $V$ as $v = a^i z_i$.

The numbers $a^i$ are called the **components** of $v$ relative to this basis.

> Think of basis vectors as a mapping from a list of scalars to a vector $v$.

Clearly, this map is surjective (every vector can be expressed in terms of components) and injective (this can be done only in one way).
So as a mapping, a basis is a bijection.

Furthermore, $z$ is a vector space isomorphism.

#### Canonical Basis

We define $\{e_i\}$ to be the **canonical basis** of $\mathcal{F}$.

Now suppose that $\Phi : \mathcal{F}^n \rightarrow V$ is a vector space isomorphism. Then the set of vectors $z_i \equiv \Phi(e_i)$ is a basis for $V$.

> The number of vectors in a basis is always equal to the dimension of the vector space.

Suppose $U_1$ and $U_2$ are subspaces of a finite-dimensional vector space, with intersection consisting only of the zero vector. Then $\dim(U_1 \oplus U_2) = \dim(U_1) + \dim(U_2)$.