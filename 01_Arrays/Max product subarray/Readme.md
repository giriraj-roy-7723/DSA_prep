Maximum Product Subarray (Optimal)

Goal:
Find the maximum product of a contiguous subarray.

Key Observations:
1) All positives → take all
2) Even number of negatives → take all
3) Odd number of negatives → drop one negative
4) Result is always a prefix OR a suffix
5) Zero breaks the subarray → reset

Core Idea:
Track product from left (prefix) and right (suffix).

Steps:
prefix = 1
suffix = 1
max_prod = -∞

for i = 0 → n-1:
    if prefix == 0: prefix = 1
    if suffix == 0: suffix = 1

    prefix *= a[i]
    suffix *= a[n-1-i]

    max_prod = max(max_prod, prefix, suffix)

Answer = max_prod

Why it works:
- Prefix handles dropping left negative
- Suffix handles dropping right negative
- Zero resets product naturally

Diagram Example:
Array: [2, 3, -2, 4]

Prefix: 2 → 6 → -12 → -48
Suffix: 4 → -8 → -24 → -48
Max = 6

Zero Case:
[2, -3, 0, -2, 4]
Reset after 0 → start fresh

Time: O(n)
Space: O(1)
