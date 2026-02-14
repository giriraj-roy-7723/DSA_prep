# Sliding Window Maximum

## 🧠 Problem
Given an array `nums` and an integer `k`, return the maximum value in every contiguous subarray (window) of size `k`.

Example:
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3  
Output: [3,3,5,5,6,7]

---

## ⚙️ Approach — Monotonic Deque

Use a deque to store **indices** in decreasing order of values.

### Steps
1. Remove indices out of window (`<= i - k`).
2. Remove smaller elements from back.
3. Push current index.
4. When `i >= k - 1`, record max from front.

---

## 🧾 Code Reference (Your Logic)

```cpp
func(arr, k) {
    list res;
    deque dq;

    for (i = 0 → n-1) {

        if (!dq.empty() && dq.front() <= i - k)
            dq.pop_front();

        while (!dq.empty() && arr[dq.back()] <= arr[i])
            dq.pop_back();

        dq.push_back(i);

        if (i >= k - 1)
            res.add(arr[dq.front()]);
    }
}
