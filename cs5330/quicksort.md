# Quicksort
#algo

Similar to merge sort, pick a random pivot.

Ideally, if the picking is good, we get amortized $O(n \log n)$ runtime.

However, in the worst possible case, we end up with $O(n^2)$ runtime if each pivot is exactly the smallest or largest unsorted element every time.