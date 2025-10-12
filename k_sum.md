# Two sum

2 main approaches:

1. Hash table, time O(n), space O(n)

   Use when order is not important, when excluding duplicates is not needed (otherwise it would be necessary to keep track of used indexes)  

2. Sorting + two pointers, time O(n log n) (if input already sorted - O(n)), space O(1)

   Use when input is already sorted, or when excluding duplicates is required

LeetCode examples:
| #    | Name                      | Type               |
| ---- | ------------------------- | ------------------ |
| 1    | Two Sum                   | hash               |
| 15   | 3Sum                      | sort + 2 pointers  |
| 18   | 4Sum                      | fix 2 + 2 pointers |
| 454  | 4Sum II                   | 2 хеш-мапы         |
| 1679 | Max Number of K-Sum Pairs | подсчёт пар        |
| 923  | 3Sum With Multiplicity    | частотный учёт     |
