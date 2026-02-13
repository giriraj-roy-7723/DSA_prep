# 📌 Next Greater Element (NGE)

## 🧠 Problem Statement

Given an array `arr[]` of size `n`, find the **Next Greater Element (NGE)** for every element.

The Next Greater Element of `arr[i]` is the **first element to the right** that is strictly greater than `arr[i]`.

If no such element exists, return `-1`.

---

## 🧾 Example

### Input
arr = [4, 12, 5, 3, 1, 2, 5, 3, 1, 2, 4, 6]

### Output

[12, -1, 6, 5, 2, 5, 6, 4, 2, 4, 6, -1]

---

# 🔎 Approach

## 🚫 Brute Force

For every element:
- Check all elements to its right.
- Find the first greater one.

Time Complexity: **O(n²)**  
Not efficient.

---

## ✅ Optimal Approach — Monotonic Stack (O(n))

We use a **Monotonic Decreasing Stack** and traverse the array from **right to left**.

### 💡 Core Idea

- Maintain a stack that keeps only useful greater elements.
- Remove all smaller elements because they can never be the answer.
- The top of the stack becomes the Next Greater Element.

---

# 🚀 Algorithm

1. Create an empty stack.
2. Create a result array `ans[n]`.
3. Traverse the array from **right to left**.
4. For each element `arr[i]`:
   - While stack is not empty and `stack.top() <= arr[i]`
     → pop from stack.
   - If stack becomes empty  
     → `ans[i] = -1`
   - Else  
     → `ans[i] = stack.top()`
   - Push `arr[i]` into stack.
5. Return `ans`.

---

