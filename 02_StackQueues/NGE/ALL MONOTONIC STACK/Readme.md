# 🧠 Monotonic Stack – Complete Cheat Sheet (All Variations)

Monotonic Stack is used when the problem asks for:

- Next / Previous
- Greater / Smaller
- Nearest element
- First bigger/smaller to left or right

If you see these words → Think MONOTONIC STACK.

---

# 🔥 The 4 Core Variations

| Problem Type        | Traverse Direction | Stack Type        |
|---------------------|-------------------|-------------------|
| Next Greater (NGE)  | Right → Left      | Decreasing Stack  |
| Next Smaller (NSE)  | Right → Left      | Increasing Stack  |
| Previous Greater    | Left → Right      | Decreasing Stack  |
| Previous Smaller    | Left → Right      | Increasing Stack  |

---

# 🧠 How To Decide Stack Type

If you want GREATER element:
→ Pop smaller elements  
→ Maintain Decreasing Stack  

If you want SMALLER element:
→ Pop greater elements  
→ Maintain Increasing Stack  

---

# 🚀 Master Template – Next Greater Element

for (int i = n-1; i >= 0; i--) {}
while (!st.empty() && st.top() <= arr[i]) {
    st.pop();
}

if (st.empty())
    ans[i] = -1;
else
    ans[i] = st.top();

st.push(arr[i]);

Time = O(n)  
Space = O(n)

---

# 🔁 Circular Next Greater Element

Difference from normal NGE:

- Traverse 2 times
- Use i % n


for (int i = 2*n - 1; i >= 0; i--) {
    while (!st.empty() && st.top() <= arr[i % n]) {
    st.pop();
}

if (i < n) {
    if (st.empty())
        ans[i] = -1;
    else
        ans[i] = st.top();
}

st.push(arr[i % n]);
}

Memory Trick:
Circular = Normal NGE + 2n loop + i % n

---

# ⏱ Why Time Complexity is O(n)

Each element:
- Pushed once
- Popped once

Total operations ≤ 2n

So:

Time  = O(n)  
Space = O(n)

---

# 🎯 Interview 10-Second Rule

If question says:

"Next"  → Traverse Right to Left  
"Previous" → Traverse Left to Right  

"Greater" → Pop smaller  
"Smaller" → Pop greater  

"Circular" → 2n loop + i % n  

Done.

---

# 🏆 Where This Pattern Appears

- Next Greater Element
- Next Smaller Element
- Stock Span
- Largest Rectangle in Histogram
- Daily Temperatures
- Trapping Rain Water (variation)

---

# ⚡ Final One-Line Summary

Next → backward  
Previous → forward  

Greater → decreasing stack  
Smaller → increasing stack  

Circular → double traversal  

Master this → You master monotonic stack.
