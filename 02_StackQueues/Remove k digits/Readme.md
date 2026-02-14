# 📘 Remove K Digits (Greedy + Monotonic Stack)

---

## 🧠 Problem

Given a numeric string `num` and an integer `k`, remove **k digits** so that the resulting number is **smallest possible**.

---

## 🔥 Core Idea

To minimize the number:

> Remove a digit if the **next digit is smaller**.

Why?  
Because digits on the left contribute more to the number’s value.  
A larger left digit increases the overall number more.

---

## ⚙️ Algorithm

1. Use a **monotonic increasing stack**.
2. Traverse each digit:
   - While:
     - `k > 0`
     - stack not empty
     - `top > current digit`
       → pop from stack  
       → decrement `k`
3. Push current digit.
4. If `k > 0` after traversal → remove last `k` digits.
5. Remove leading zeros.
6. If result becomes empty → return `"0"`.

---

## 📐 Why It Works

We always remove the **leftmost bigger digit first**  
→ Because reducing higher place values minimizes the number fastest.

Greedy + Local optimal choice = Global minimum.

---

## 🧮 Example

```
num = "1432219", k = 3
```

Removals:

```
4 > 3 → remove 4
3 > 2 → remove 3
2 > 1 → remove 2
```

Result:

```
"1219"
```

---

## ⏱ Complexity

```
Time  : O(n)
Space : O(n)
```

Each digit is pushed and popped at most once.

---

## 🎯 One-Line Memory Trick

> “If next digit is smaller, remove the previous bigger digit.”

Monotonic Increasing Stack → Smallest Number.
