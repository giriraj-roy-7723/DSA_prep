

### Core Insight: Exact K = At Most K − At Most (K-1)

Directly counting subarrays with **exactly K** distinct elements is hard because a sliding window naturally handles "at most K" — once you've satisfied the constraint, shrinking from the left is ambiguous (you might undershoot).

So the trick is:

```
exactly(K) = atMost(K) - atMost(K-1)
```

`subcount(nums, k)` counts subarrays with **at most k** distinct integers. Subtracting removes all subarrays with at most K-1 distinct integers, leaving only those with **exactly K**.

---

### Why `count += r - l + 1`

At any point in the loop, your window is `[l, r]`. You've just expanded it by moving `r` right, and you've already shrunk `l` so the window has at most `k` distinct elements.

**All subarrays ending at `r` that start anywhere in `[l, r]` are valid.** Those are:
```
[l, r], [l+1, r], [l+2, r], ..., [r, r]
```
That's exactly `r - l + 1` subarrays.

**Example walkthrough** with `nums = [1,2,1,2,3]`, `k=2`:

| r | window | l | new subarrays ending at r | count |
|---|--------|---|--------------------------|-------|
| 0 | [1] | 0 | [1] → 1 | 1 |
| 1 | [1,2] | 0 | [1,2],[2] → 2 | 3 |
| 2 | [1,2,1] | 0 | [1,2,1],[2,1],[1] → 3 | 6 |
| 3 | [1,2,1,2] | 0 | 4 subarrays | 10 |
| 4 | [2,3] | 3 | [2,3],[3] → 2 | 12 |

`subcount(nums, 2)` = 12, `subcount(nums, 1)` = 5, answer = **7** ✓

---

### Why this is elegant

The sliding window guarantees that at every step, `l` is the **leftmost valid start** for a window ending at `r`. Every index between `l` and `r` is also a valid start (removing a prefix can only reduce distinct count, keeping it ≤ k). So you're counting all valid subarrays ending at `r` in **O(1)** per step rather than checking each one.

**Time complexity:** O(n) — each element enters and exits the window at most once.