Problem:
Find two numbers whose sum equals the target.

Better approach (HashMap):
Use when the array is unsorted
and you need the answer in one pass.

Idea:
Store each number and check if (target - current) already exists.

Why it works:
You trade extra space to avoid nested loops.

Time: O(n)
Space: O(n)

Optimal approach (Sort + Two Pointers):
Use when modifying the array is allowed
or when space must be minimized.

Idea:
Sort the array.
Left pointer increases sum,
right pointer decreases sum.

Steps:
if sum < target → move left
if sum > target → move right
if equal → answer found

Time: O(n log n)
Space: O(1) extra

Warning:
Sorting changes indices.
Not suitable if original indices are required.
