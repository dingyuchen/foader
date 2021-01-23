# Recursive Binomial Coefficients

## Theorem
$$\binom{n}{r} = \binom{n-1}{r-1} + \binom{n-1}{r}$$

## Proof
### Combinatorial Argument
Sum of ways where some object is chosen and when it is not.

If object 1 is chosen, then there are $\binom{n -1}{r-1}$ ways of selecting $r-1$ objects from the remaining $n-1$ objects.

If object 1 is not chosen, then there are $\binom{n -1}{r}$ ways of selecting $r$ objects from the remaining $n-1$ objects.

Thus, $\binom{n}{r} = \binom{n-1}{r-1} + \binom{n-1}{r}$