Three Sum (i, j, k — Two Pointer)

Goal:
Find all unique triplets where a[i] + a[j] + a[k] = 0

Core Idea:
Fix i → solve remaining using Two Sum (j, k)

Steps:
1) Sort the array
2) For i = 0 → n-3:
   - skip duplicate i
   - j = i + 1, k = n - 1

Pointer Movement:
sum = a[i] + a[j] + a[k]

if sum < 0 → j++   (need bigger sum)
if sum > 0 → k--   (need smaller sum)
if sum == 0:
   store triplet
   j++, k--
   skip duplicate j & k

Diagram Example:
Sorted: [-4, -1, -1, 0, 1, 2]

i=-1
 j=-1        k=2
[-1, -1, 0, 1, 2]
sum = 0 → store

Why it works:
Sorting gives order → two pointers adjust sum optimally

Time: O(n²)
Space: O(1) (excluding output)
