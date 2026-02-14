# 📘 Stock Span Problem (Monotonic Stack)

---

## 🧠 Problem

Given daily stock prices, compute the **span** of each day.

👉 Span = Number of consecutive days (including today)  
where `price ≤ today’s price`.

---

## 🧾 Example

```
prices = [100, 80, 60, 70, 60, 75, 85]
span   = [  1,  1,  1,  2,  1,  4,  6]
```

---

## 🔥 Core Idea

We need to find:

👉 **Previous Greater Element (PGE)** index

Because:

```
Span = i - PGE_index
```

If no greater element exists:

```
Span = i + 1
```

---

## ⚙️ Algorithm

Use a stack storing **indices**.

For each day `i`:

1️⃣ While stack not empty AND  
   `price[stack.top] ≤ price[i]`  
   → pop (remove smaller or equal prices)

2️⃣ If stack empty  
   → span = `i + 1`

   Else  
   → span = `i - stack.top()`

3️⃣ Push current index `i` into stack

---

## 📐 Why It Works

We remove all smaller or equal prices  
because they cannot block future spans.

The first remaining element on stack  
is the nearest greater price to the left.

Distance from that index gives span.

---

## ⏱ Complexity

```
Time  : O(n)
Space : O(n)
```

Each index:
- Pushed once
- Popped once

---

## 🧠 Memory Trick

👉 Pop all smaller or equal prices  
👉 Distance to previous greater gives span

---

## 🎯 One-Line Concept

Span = distance to previous greater price.

Monotonic Decreasing Stack → Span problems become easy.
```
