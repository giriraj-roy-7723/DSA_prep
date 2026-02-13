Balanced Parenthesis (Using Stack)

Goal:
Check if brackets are properly opened and closed.

Valid pairs:
()  {}  []

Core Idea:
Opening brackets go into stack.
Closing brackets must match the top.

Steps:
1) Create empty stack
2) Traverse string:
   if opening bracket:
       push into stack

   if closing bracket:
       if stack empty → invalid
       pop top
       if popped != matching opening → invalid

3) After loop:
   if stack empty → valid
   else → invalid

Why it works:
Stack follows LIFO.
Last opened must close first.

Example:
Input: "({[]})"

Push ( → push { → push [
Meet ] → pop [
Meet } → pop {
Meet ) → pop (
Stack empty → balanced

Time: O(n)
Space: O(n)
