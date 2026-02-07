Next Permutation (Optimal)

Goal:
Rearrange numbers into the next lexicographically greater permutation.
If not possible → return smallest (sorted ascending).

Core Idea:
Find the first place from right where order breaks.

Steps:
1) Find index i from right such that:
   a[i] < a[i+1]
   (first decreasing element from right)

2) If no such i:
   reverse whole array → done

3) Find index j from right such that:
   a[j] > a[i]

4) Swap a[i] and a[j]

5) Reverse subarray from i+1 to end

Why it works:
Right side is already the largest possible.
Swap makes it just bigger, reverse makes it smallest.

Time: O(n)
Space: O(1)
