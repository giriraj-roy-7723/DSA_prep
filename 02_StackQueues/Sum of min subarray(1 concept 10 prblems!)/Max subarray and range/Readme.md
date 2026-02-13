# 📈 Sum of Subarray Maximums (Monotonic Stack – PGE + NGE)

---

## 🧠 Problem

Given an array `arr[]`, compute the **sum of maximum elements of all subarrays**.

This is commonly used to solve:

```
Sum of Subarray Ranges =
Sum of Subarray Maximums − Sum of Subarray Minimums
```

---

## 🧾 Example

Input:
```
arr = [3,1,2,4]
```

Subarrays and maximums:
```
[3] → 3  
[3,1] → 3  
[3,1,2] → 3  
[3,1,2,4] → 4  
[1] → 1  
[1,2] → 2  
[1,2,4] → 4  
[2] → 2  
[2,4] → 4  
[4] → 4  
```

Total = **30**

---

# 🔥 Core Idea

Instead of generating all subarrays (O(n²)),  
we calculate **contribution of each element**.

For each element:

```
Contribution = arr[i] * (# subarrays where arr[i] is maximum)
```

To compute how many subarrays choose `arr[i]` as maximum:

We find:
- PGE → Previous Greater Element
- NGE → Next Greater Element

---

# 🧠 Key Formula

Let:

```
left  = distance to Previous Greater  
right = distance to Next Greater
```

Then:

```
Contribution of arr[i] = arr[i] * left * right
```

Final Answer = sum of all contributions

---

# 🚀 How To Compute Left & Right

## 1️⃣ Previous Greater Element (PGE)

Traverse **Left → Right**  
Maintain **Decreasing Stack**

Pop while:
```
arr[stack.top()] < arr[i]
```

Distance:
```
left[i] = i - previousGreaterIndex
```

If none:
```
left[i] = i + 1
```

---

## 2️⃣ Next Greater Element (NGE)

Traverse **Right → Left**  
Maintain **Decreasing Stack**

Pop while:
```
arr[stack.top()] <= arr[i]
```

Distance:
```
right[i] = nextGreaterIndex - i
```

If none:
```
right[i] = n - i
```

⚠ Important:
- For **PGE use `<`**
- For **NGE use `<=`**

This avoids double counting duplicates.

---

# 💻 C++ Code

```cpp
long long sumSubarrayMax(vector<int>& arr) {
    int n = arr.size();
    vector<long long> left(n), right(n);
    stack<int> st;

    // Previous Greater (strict)
    for(int i = 0; i < n; i++) {
        while(!st.empty() && arr[st.top()] < arr[i])
            st.pop();

        left[i] = st.empty() ? i + 1 : i - st.top();
        st.push(i);
    }

    while(!st.empty()) st.pop();

    // Next Greater (non-strict)
    for(int i = n - 1; i >= 0; i--) {
        while(!st.empty() && arr[st.top()] <= arr[i])
            st.pop();

        right[i] = st.empty() ? n - i : st.top() - i;
        st.push(i);
    }

    long long sum = 0;

    for(int i = 0; i < n; i++)
        sum += arr[i] * left[i] * right[i];

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

Maximum problem → Decreasing stack

Find:
- PGE (<)
- NGE (<=)

Formula:

```
arr[i] * left * right
```

Multiply contributions. Done.

---

# 🎯 Final Connection: Sum of Subarray Ranges

To solve:

```
Sum of Subarray Ranges
```

Just compute:

```
SumMax − SumMin
```

Where:
- SumMax → use decreasing stack (this file)
- SumMin → use increasing stack version

---

# ⚡ 10-Second Recall

Minimum → Increasing stack  
Maximum → Decreasing stack  

Contribution formula:

```
arr[i] * left * right
```

Ranges problem?

```
Max − Min
```

That’s it.

---

**Monotonic Stack Pattern = Contribution Counting.**

Master Min + Max → Subarray Ranges becomes trivial.
