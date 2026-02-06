Use XOR when you need to cancel out duplicate numbers
or find the single different element.

Key rules:
x ^ x = 0   (same numbers cancel)
x ^ 0 = x   (zero changes nothing)
XOR order does not matter.

Why it works:
All pairs cancel out, only the unique value remains.

Common use:
Find the element that appears once when others appear twice.

Does not work when elements appear more than twice
or when order matters.
