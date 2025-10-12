# Two sum

2 main approaches:

1. Hash table, time O(n), space O(n)
   Use when order is not important, when excluding duplicates is not needed (otherwise it would be necessary to keep track of used indexes)  
2. Sorting + two pointers, time O(n log n) (if input already sorted - O(n)), space O(1)
   Use when input is already sorted, or when excluding duplicates is required
