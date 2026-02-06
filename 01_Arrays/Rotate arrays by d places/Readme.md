Use this when you need to rotate an array by D positions in-place
without using extra space.

Idea:
Rotation can be done by reversing parts of the array.

Steps:
reverse first D elements
reverse remaining N-D elements
reverse the whole array

Why it works:
Each part goes to its correct position after the final reverse.

Important:
If D > N, do D = D % N first.

Works only when order matters and array is continuous.
