Longest Consecutive Sequence (Optimal)

Goal:
Find length of the longest sequence of consecutive integers (order doesn't matter).

Core Idea:
Only start counting from numbers that are sequence starters.

Rule:
A number is a starter if (num - 1) does NOT exist.

Steps:
1) Put all numbers into a HashSet
2) For each num:
   if (num - 1) not in set:
       start a sequence
       count forward: num+1, num+2, ...

3) Track maximum length

Why it works:
Each number is visited at most once.
No re-counting of middle elements.

Time: O(n)
Space: O(n)
