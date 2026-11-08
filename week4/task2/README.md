README Report: Intersection of Two Linked Lists

1. Problem

I get the heads of two linked lists. At some point they can join and share the same ending. I need to return the first shared node (the same node, not just the same value). If they never join, I return null.

2. Approach

I use two pointers: a starts at the head of list A, b starts at the head of list B.
- Both pointers move one step at a time.
- When a pointer reaches the end, it jumps to the head of the other list.
- I stop when both pointers point to the same node.

Why it works: each pointer walks the same total distance (length of A plus length of B). So the difference in lengths disappears, and both pointers arrive at the shared node at the same time. If there is no shared node, both pointers become null at the same time, and I return null.

Example: A = 4, 1, 8, 4, 5 and B = 5, 6, 1, 8, 4, 5. The ending 8, 4, 5 is shared.
- Pointer a goes: 4, 1, 8, 4, 5, then null, then jumps to B: 5, 6, 1, 8.
- Pointer b goes: 5, 6, 1, 8, 4, 5, then null, then jumps to A: 4, 1, 8.
- After 9 moves both pointers stand on the shared node with value 8.

Result: the node with value 8.

3. Time Complexity

Time Complexity: O(m + n)

Each pointer goes through list A and list B at most one time, so it is m + n steps. I use only two pointers, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? Not in time. We need to read both lists, so O(m + n) is the minimum.
- What would I need to change? Nothing, this is already the improved solution. The brute-force way (for each node of A, check all of B) is O(m * n). The HashSet way (save nodes of A, then check B) is O(m + n) time but uses O(m) memory.
- What complexity could the improved solution achieve? O(m + n) time and O(1) memory. This is what my solution has.
