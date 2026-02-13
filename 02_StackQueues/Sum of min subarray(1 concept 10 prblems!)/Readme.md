# 📉 Sum of Subarray Minimums (Monotonic Stack – PSE + NSE)

---

## 🧠 Problem

Given an array `arr[]`, return the **sum of minimum elements of all subarrays**.

---

## 🧾 Example

Input:
```
arr = [3,1,2,4]
```

Output:
```
17
```

Subarrays:
```
[3] → 3  
[3,1] → 1  
[3,1,2] → 1  
[3,1,2,4] → 1  
[1] → 1  
[1,2] → 1  
[1,2,4] → 1  
[2] → 2  
[2,4] → 2  
[4] → 4  
```

Total = **17**

---

# 🔥 Core Idea

Instead of generating all subarrays (O(n²)),  
we calculate **contribution of each element**.

For each element:

```
Contribution = arr[i] * (# subarrays where arr[i] is minimum)
```

To find how many subarrays where `arr[i]` is minimum:

We find:
- PSE → Previous Smaller Element
- NSE → Next Smaller Element

---

# 🧠 Key Formula

Let:

```
left  = distance to Previous Smaller  
right = distance to Next Smaller
```

Then:

```
Contribution of arr[i] = arr[i] * left * right
```

Final Answer = sum of all contributions

---

# 🚀 How To Compute Left & Right

## 1️⃣ Find Previous Smaller Element (PSE)

Traverse **Left → Right**  
Maintain **Increasing Stack**

Pop while:
```
stack.top() > arr[i]
```

Distance:
```
left[i] = i - previousSmallerIndex
```

If none:
```
left[i] = i + 1
```

---

## 2️⃣ Find Next Smaller Element (NSE)

Traverse **Right → Left**  
Maintain **Increasing Stack**

Pop while:
```
stack.top() >= arr[i]
```

Distance:
```
right[i] = nextSmallerIndex - i
```

If none:
```
right[i] = n - i
```

⚠ Important:
- For **PSE use `>`**
- For **NSE use `>=`**

This avoids double counting duplicates.

---

# 💻 C++ Code

```cpp
int sumSubarrayMins(vector<int>& arr) {
    int n = arr.size();
    vector<int> left(n), right(n);
    stack<int> st;

    // Previous Smaller (strict)
    for(int i = 0; i < n; i++) {
        while(!st.empty() && arr[st.top()] > arr[i])
            st.pop();

        left[i] = st.empty() ? i + 1 : i - st.top();
        st.push(i);
    }

    while(!st.empty()) st.pop();

    // Next Smaller (non-strict)
    for(int i = n - 1; i >= 0; i--) {
        while(!st.empty() && arr[st.top()] >= arr[i])
            st.pop();

        right[i] = st.empty() ? n - i : st.top() - i;
        st.push(i);
    }

    long long sum = 0;
    int mod = 1e9 + 7;

    for(int i = 0; i < n; i++) {
        sum = (sum + (long long)arr[i] * left[i] * right[i]) % mod;
    }

    return sum;
}
```

---

# ⏱ Complexity

```
Time  = O(n)
Space = O(n)
```

Each element:
- Pushed once
- Popped once

Total operations ≤ 2n

---

# 🧠 Memory Trick

We don't build subarrays.

We count:

How many subarrays choose this element as minimum?

Formula to remember:

```
arr[i] * left * right
```

Left  → distance to previous smaller  
Right → distance to next smaller  

Multiply everything. Done.

---

# ⚡ Interview 10-Second Recall

Minimum problem → Increasing stack

Find:
- PSE (>)
- NSE (>=)

Contribution:

```
arr[i] * left * right
```

That’s it.

---

# 🔥 What Next?

You can extend this pattern to:

- 🔥 Sum of Subarray Maximums  
- 📊 Combined Min + Max Master Sheet  
- 🧠 Deep intuition: Why strict/non-strict inequality matters  

---

**Monotonic Stack Pattern = Contribution Counting.**

Master this once → 10+ problems unlocked.
