README Report: Linked List Cycle

1. Problem

I get the head of a linked list. I need to check if the list has a cycle. A cycle means that some node points back to an earlier node, so we can go around forever and never reach the end.

2. Approach

I use two pointers: slow moves 1 step at a time, fast moves 2 steps at a time. Both start at the head.

- If there is no cycle, fast reaches the end of the list (null), and I return false.
- If there is a cycle, both pointers enter it. Fast moves faster, so it catches up with slow from behind. Each step the distance between them gets smaller by 1, so they must meet. When they stand on the same node, I return true.

Example 1: 3 -> 2 -> 0 -> -4, and the last node points back to 2
- Start: slow is 3, fast is 3.
- Step 1: slow is 2, fast is 0.
- Step 2: slow is 0, fast is 2 (fast went from 0 to -4 to 2).
- Step 3: slow is -4, fast is -4 (fast went from 2 to 0 to -4).
- They are the same node, so the answer is true.

Example 2: 1 -> 2 -> null
- Start: slow is 1, fast is 1.
- Step 1: slow is 2, fast is null.
- Fast reached the end, so the answer is false.

3. Time Complexity

Time Complexity: O(n)

If there is no cycle, fast reaches the end after about n / 2 steps. If there is a cycle, slow does not make more than one full round of the list before fast catches it, so the number of steps is still linear. I use only two pointers, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? Not in time, because in the worst case we must walk through the whole list. A simpler idea is a HashSet of visited nodes. It is also O(n) time, but it uses O(n) memory.
- What would I need to change? Nothing. This solution already uses the best memory. The HashSet way is easier to understand, but it is worse in memory.
- What complexity could the improved solution achieve? O(n) time and O(1) memory. This is what my solution has.
