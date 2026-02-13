# 📘 Largest Rectangle in Histogram (Monotonic Stack)

---

## 🧠 Core Idea

For every bar `i`, treat it as the **minimum height** of a rectangle.

Expand it:
- Left → until **Previous Smaller Element (PSE)**
- Right → until **Next Smaller Element (NSE)**

This gives the maximum width where `arr[i]` is the limiting height.

---

## 📐 Formula

```
width  = NSE[i] - PSE[i] - 1
area   = arr[i] * width
answer = max(area for all i)
```

---

## 🔍 Why `-1`?

Because:
- `PSE[i]` → index of smaller bar on left (excluded)
- `NSE[i]` → index of smaller bar on right (excluded)

So usable width lies strictly between them.

---

## 🧮 Example

Heights:
```
[2, 1, 5, 6, 2, 3]
```

For height `5`:

```
PSE = index of 1
NSE = index of 2
width = 4 - 1 - 1 = 2
area = 5 × 2 = 10
```

Maximum Area = **10**

---

## ⚙️ Algorithm Steps

1. Compute `PSE` using a monotonic increasing stack.
2. Compute `NSE` using a monotonic increasing stack.
3. For each index:

```
area = arr[i] * (nse[i] - pse[i] - 1)
```

4. Return maximum area.

---

## ⏱ Complexity

```
Time  : O(n)
Space : O(n)
```

Each index is pushed and popped at most once.

---

## 🎯 One-Line Memory Trick

> “Each bar expands left and right until a smaller bar appears.”

Master PSE + NSE → Histogram becomes easy.
