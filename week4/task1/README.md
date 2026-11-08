README Report: Remove Duplicates from Sorted List

1. Problem

I get a sorted linked list. I need to remove repeated values, so each value stays only once. Then I return the list.

2. Approach

The list is sorted, so equal values always stand next to each other.

I use one pointer called node. I look at the node and the next node:
- If their values are equal, I delete the next node and I stay on the same node. The new next node can also be the same value.
- If they are different, I move the pointer forward.
- I stop when there is no next node.

Example: 1 -> 1 -> 2 -> 3 -> 3
- Step 1: node is 1, next is 1. Equal, so I delete the next one. List: 1 -> 2 -> 3 -> 3.
- Step 2: node is 1, next is 2. Different, so I move. Node is 2.
- Step 3: node is 2, next is 3. Different, so I move. Node is 3.
- Step 4: node is 3, next is 3. Equal, so I delete the next one. List: 1 -> 2 -> 3.
- Step 5: node is 3, there is no next node. I stop.

Result: 1 -> 2 -> 3

3. Time Complexity

Time Complexity: O(n)

In every step I either delete one node or move one step forward. So I make at most n steps. I use only one pointer, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? No. We must see every node at least once, so O(n) is the best time.
- What would I need to change? Nothing. A HashSet of seen values would also work, but it uses O(n) extra memory, so it is worse.
- What complexity could the improved solution achieve? The same: O(n) time and O(1) memory.
