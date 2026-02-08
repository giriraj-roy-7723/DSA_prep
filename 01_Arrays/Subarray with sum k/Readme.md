Count Subarrays with Sum = K (Optimal)

Goal:
Count number of subarrays whose sum equals K.

Core Idea:
If prefix_sum[j] - prefix_sum[i] = K
→ prefix_sum[i] = prefix_sum[j] - K

Use a HashMap to store prefix_sum frequencies.

Steps:
1) map = {0 : 1}   // empty prefix
2) prefix_sum = 0
3) count = 0

for x in array:
    prefix_sum += x

    if (prefix_sum - K) exists in map:
        count += map[prefix_sum - K]

    map[prefix_sum]++

Answer = count

Why it works:
Every valid subarray is detected by a previous prefix.

Time: O(n)
Space: O(n)
