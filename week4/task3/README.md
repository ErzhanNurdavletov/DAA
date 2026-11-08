README Report: Remove Linked List Elements

1. Problem

I get a linked list and a number val. I need to remove all nodes that have this value and return the new head of the list.

2. Approach

The head can also be removed, and this makes the code harder. To fix this, I add a dummy node before the head.

I use a pointer called current. It always stands before the node that I check:
- If the next node has the value val, I skip it. I do not move current, because the new next node can also be removed.
- If the next node has another value, I move current forward.
- At the end I return the node after dummy. This is the real head.

Example: 1 -> 2 -> 6 -> 3 -> 6, val = 6
- Step 1: next is 1. Keep it, move.
- Step 2: next is 2. Keep it, move.
- Step 3: next is 6. Remove it. List: 1 -> 2 -> 3 -> 6.
- Step 4: next is 3. Keep it, move.
- Step 5: next is 6. Remove it. List: 1 -> 2 -> 3.
- Step 6: there is no next node. I stop.

Result: 1 -> 2 -> 3

Special case: 7 -> 7 -> 7 with val = 7. All nodes are removed, so the result is an empty list.

3. Time Complexity

Time Complexity: O(n)

In every step I either remove one node or move one step forward. So each node is handled one time. I use only two pointers, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? No. We must check every node, so O(n) is the best time. Memory is already O(1).
- What would I need to change? Nothing. Other ways, like making a new list or using recursion, need O(n) extra memory, so they are worse.
- What complexity could the improved solution achieve? The same: O(n) time and O(1) memory.
