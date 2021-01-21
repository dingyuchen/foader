# Treaps

#data-structures

Treaps are made of (value, priority) pairs.

Priority is a random number.

> For any set of (key, priority) pairs, there is a unique treap containing that set.
> There is always a highest priority - the priority forms a heap 

## How to build a Treap?
1. Given a key, assign a random priority to each
2. Find key with maximum priority. Place at root.
3. Find keys with a smaller key value, recursively build treap as left child of root. Same for larger keys for the right child.
The BST branches similar to the quicksort algorithm

## Guarantee
- After $n$ insertions, the depth of a treap is $O(\log n)$ with high probability. So subsequent `insert`, `search` and `delete` operations take $O(\log n)$ time.
- In **any** sequence of $n$ operations, each operation takes $O(\log n)$ time with high probability.