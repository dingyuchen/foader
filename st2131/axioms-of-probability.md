# Axioms of Probability

## Preface
### Sample Space
Consider an experiment whose outcome is not predictable with certainty.

The set of all possible outcomes of the experiment is known as the _sample space_.

> Sample space can be uncountable (eg. age of a tree)

### Event
Any subset of a [sample space](#sample-space)

### Laws on Sets
- Commutative Laws
- Associative Laws
- Distributive Laws
- De Morgan's Laws

## Definition
One way of defining the probability of an event is in terms of its _relative frequency_:

$$ P(E) = \lim_{n \rightarrow \inf} \frac{n(E)}{n} $$

### Problems with this definition:
1. How do we know that $\frac{n(E)}{n}$ will converge?
2. How do we know that $\frac{n(E)}{n}$ will converge to the same if the experiment is repeatedly performed a second time?

### Better Axioms

Consider an experiment whose sample space is $S$. For each event $E$ of the sample space $S$, we assume that a number $P(E)$ is defined and satisfies the following 3 [[axiom]]s:

1. $0 \leq P(E) \leq 1$
2. $P(S) = 1$
3. For any sequence of mutually exclusive events $E_1, E_2, ...$, $$P(\bigcup^{\infty}_{i = 1} E(i)) = \sum^{\infty}_{i = 1} P(E_i)$$

> The definitions of probability are mathematical definitions. They tell us which set functions can be called probability functions. They do not tell us the value of probability assigned to a given event.

## Strong Law of Large Numbers

If an experiment is repeated over and over again, then with probability 1, the proportion of time during which any specific event $E$ occurs will equal $P(E)$.

## Inclusion-Exclusion Identity
[[inclusion-exclusion-identity]]

### Matching Hats Problem

Suppose that each of $N$ men at a party throws his hat into the center of the room.
The hats are first mized up, and then each man randomly selects a hat.
What is the probability that

1. none of the men selects his own hat
2. exactly $k$ of the men select their own hat

> Can also be expressed as a recursive equation.


## Probability as a Continuous Set Function

Suppose an increasing sequence of events:

$$E_1 \subset E_2 \subset ... \subset E_n \subset ...$$

Denote $\lim_{n \rightarrow \infty} E_n = \bigcup^\infty_{i = 1} E_i$

$$E_1 \supset E_2 \supset ... \supset E_n \supset ...$$

Denote $\lim_{n \rightarrow \infty} E_n = \bigcap^\infty_{i = 1} E_i$

> For increasing or decreasing sequence of events,
> 
> $$\lim_{n \rightarrow \infty} P(E_n) = P(\lim_{n \rightarrow \infty} E_n)$$

### Proof

Set $F_i = E_i - E_{i - 1}$

Then union of $E$ is the same as sum of $F$ since $F$ is mutually exclusive.


[//begin]: # "Autogenerated link references for markdown compatibility"
[axiom]: axiom "Axiom"
[inclusion-exclusion-identity]: inclusion-exclusion-identity "Inclusion-Exclusion Identity"
[//end]: # "Autogenerated link references"