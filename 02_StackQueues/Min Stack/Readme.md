Implement Min Stack (Get minimum in O(1))

Goal:
Support push, pop, top, getMin in O(1) time.

Core Idea:
Keep track of minimum along with values.

-------------------------------------

Approach 1: Two Stacks

Stack1 → normal values
Stack2 → current minimums

Push:
- push value into Stack1
- if Stack2 empty OR value <= top(Stack2):
      push into Stack2

Pop:
- if popped value == top(Stack2):
      pop from Stack2

getMin:
- return top(Stack2)

Why it works:
Stack2 always stores valid minimums.

Time: O(1)
Space: O(n)

-------------------------------------

Approach 2: One Stack (Space Optimized)

Store modified values when new min appears.

If new_val < current_min:
    push(2*new_val - current_min)
    update current_min = new_val
Else:
    push normally

During pop:
If popped < current_min:
    original_min = current_min
    current_min = 2*current_min - popped

Why it works:
Encoded values help recover previous minimum.

Time: O(1)
Space: O(1) extra
