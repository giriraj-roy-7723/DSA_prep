# 🌧 Trapping Rain Water

## 🧠 Problem

Given an array `height[]` representing elevation bars, compute how much water can be trapped after raining.

---

## 🧾 Example

Input:
height = [0,1,0,2,1,0,1,3,2,1,2,1]

Output:6


---

# 🔥 Core Idea

Water trapped at index `i` depends on:

Water[i] = min(Max height to left, Max height to right) - height[i]


If result < 0 → take 0

The amount of water above a bar is limited by the **shorter boundary wall**.

---

# ✅ Approach 1: Concept Using Left & Right Maximum

For each index:
- Find maximum height on the left
- Find maximum height on the right
- Apply formula:

water += min(leftMax, rightMax) - height[i]



Naive implementation:
- Time = O(n²)
- Space = O(1)

This gives the core understanding of the problem.

---

# 🚀 Approach 2: Prefix Max & Suffix Max Arrays (Optimal)

## Step 1: Build Prefix Max Array

prefixMax[i] = max(height[0] to height[i])


## Step 2: Build Suffix Max Array

suffixMax[i] = max(height[i] to height[n-1])


## Step 3: Compute Water


water += min(prefixMax[i], suffixMax[i]) - height[i]

---

# 💻 C++ Code (Prefix + Suffix Method)

```cpp
int trap(vector<int>& height) {
    int n = height.size();
    if(n == 0) return 0;

    vector<int> prefix(n), suffix(n);

    // Build prefix max
    prefix[0] = height[0];
    for(int i = 1; i < n; i++)
        prefix[i] = max(prefix[i-1], height[i]);

    // Build suffix max
    suffix[n-1] = height[n-1];
    for(int i = n-2; i >= 0; i--)
        suffix[i] = max(suffix[i+1], height[i]);

    // Calculate trapped water
    int water = 0;
    for(int i = 0; i < n; i++)
        water += min(prefix[i], suffix[i]) - height[i];

    return water;
}

Complexity

Time = O(n)
Space = O(n)