Majority Element (Element appearing > n/2 times)

Better Approach (HashMap):
Count frequency of each element.
If any count > n/2 → that is the answer.

Why it works:
Majority element dominates total count.

Time: O(n)
Space: O(n)

---

Optimal Approach (Moore’s Voting Algorithm):

Idea:
If an element appears more than n/2 times,
it cannot be canceled out by other elements.

Steps:
candidate = None
count = 0

for x in array:
    if count == 0:
        candidate = x
        count = 1
    else if x == candidate:
        count++
    else:
        count--

After pass:
candidate is the potential majority.

(Optionally verify by counting again)

Time: O(n)
Space: O(1)
