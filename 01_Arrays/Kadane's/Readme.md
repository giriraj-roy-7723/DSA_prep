Maximum Subarray Sum (Kadane’s Algorithm)

Goal:
Find the maximum sum of a contiguous subarray.

Core Idea:
At every index, decide:
- continue the previous subarray
- or start fresh from current element

Rule:
If current_sum becomes negative → drop it.

Steps:
current_sum = 0
max_sum = -∞

for x in array:
    current_sum += x
    max_sum = max(max_sum, current_sum)
    if current_sum < 0:
        current_sum = 0

Answer = max_sum

Why it works:
A negative prefix only reduces future sums.

Time: O(n)
Space: O(1)
