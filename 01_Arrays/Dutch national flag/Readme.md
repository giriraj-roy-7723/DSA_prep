Dutch National Flag Algorithm (Sort 0s, 1s, 2s)

Use when the array contains only 0, 1, 2
and you want in-place sorting in one pass.

Idea:
Split array into 3 regions:
0s on the left, 1s in the middle, 2s on the right.

Pointers:
low  -> boundary for 0s
mid  -> current element
high -> boundary for 2s

Process while mid <= high:
if a[mid] == 0:
    swap(a[low], a[mid])
    low++, mid++

if a[mid] == 1:
    mid++

if a[mid] == 2:
    swap(a[mid], a[high])
    high--   (mid stays, needs recheck)

Result:
all 0s | all 1s | all 2s

Time: O(n)
Space: O(1)
