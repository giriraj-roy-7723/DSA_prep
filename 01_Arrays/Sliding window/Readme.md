Use sliding window when the problem asks about a
continuous subarray or substring
and you can move forward instead of restarting every time.

Core idea:
Expand with the right pointer,
shrink with the left pointer only when the condition breaks.

Think like this:
right adds elements,
left removes elements to fix the condition.

Steps:
move right
update data
while condition is broken:
    move left
    update data
update answer

Works best for:
longest / shortest / count of valid subarrays.

Does not work when subarray order doesn't matter
or when all subsets must be tried.
