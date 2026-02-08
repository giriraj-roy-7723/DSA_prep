Four Sum (i, j, k, l — Optimal)

Goal:
Find all unique quadruplets where:
a[i] + a[j] + a[k] + a[l] = target

Core Idea:
Fix two indices → reduce to Two Sum using two pointers.

Steps:
1) Sort the array
2) For i = 0 → n-4:
   - skip duplicate i
3) For j = i+1 → n-3:
   - skip duplicate j
   - k = j + 1, l = n - 1

Pointer Movement:
sum = a[i] + a[j] + a[k] + a[l]

if sum < target → k++   (need bigger sum)
if sum > target → l--   (need smaller sum)
if sum == target:
   store quadruplet
   k++, l--
   skip duplicate k & l

Diagram Example:
Sorted: [-2, -1, 0, 0, 1, 2], target = 0

i=-2  j=-1
        k=0        l=2
[-2, -1, 0, 0, 1, 2]
sum = -1 → k++

Why it works:
Sorting + fixed indices + two pointers avoid O(n⁴)

Time: O(n³)
Space: O(1) (excluding output)
