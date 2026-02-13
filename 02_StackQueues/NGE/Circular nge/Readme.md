# 🔁 Circular Next Greater Element (NGE)

## 🧠 Problem

Given a circular array `arr[]`, find the Next Greater Element for every element.

🔹 The array is circular → after last index, it continues from index `0`.  
🔹 If no greater element exists → return `-1`.

---

## 🧾 Example

Input:
arr = [1, 2, 1]

Output:

[2, -1, 2]

Explanation:
- For first `1` → next greater is `2`
- For `2` → no greater element → `-1`
- For last `1` → circular → next greater is `2`

---

# 🚀 Core Idea

Normal NGE = traverse once (right → left)

Circular NGE = simulate **2 traversals**

👉 We pretend the array exists twice.

Instead of physically doubling it, we use:


for (i = 2n - 1 → 0)

And access elements using:

arr[i % n]


---

# 🔥 Algorithm (Monotonic Stack)

1. Create stack.
2. Create result array `ans[n]`.
3. Traverse from `2n - 1` down to `0`.
4. For each index:
   - While stack not empty AND `stack.top() <= arr[i % n]`
       → pop
   - If `i < n`:
       - If stack empty → `ans[i] = -1`
       - Else → `ans[i] = stack.top()`
   - Push `arr[i % n]` into stack.

Return `ans`.

---

# 💻 C++ Code

```cpp
vector<int> nextGreaterElements(vector<int>& arr) {
    int n = arr.size();
    vector<int> ans(n);
    stack<int> st;

    for(int i = 2*n - 1; i >= 0; i--) {

        while(!st.empty() && st.top() <= arr[i % n]) {
            st.pop();
        }

        if(i < n) {
            if(st.empty())
                ans[i] = -1;
            else
                ans[i] = st.top();
        }

        st.push(arr[i % n]);
    }

    return ans;
}
