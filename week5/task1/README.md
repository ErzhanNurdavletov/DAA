README Report: Sort List

1. Problem

I get the head of a linked list with unsorted numbers. I need to sort the list in ascending order and return it.

2. Approach

I use merge sort. It is good for linked lists, because merging does not need random access.

- If the list is empty or has one node, it is already sorted, so I return it.
- I find the middle with two pointers: slow moves 1 step, fast moves 2 steps. Then I cut the list into two halves.
- I sort each half with the same method (recursion).
- I merge the two sorted halves into one sorted list: I always take the smaller first node.

Example: 4 -> 2 -> 1 -> 3
- Cut in the middle: 4 -> 2 and 1 -> 3.
- Cut again: 4, 2, 1, 3. Each one is a single node, so it is sorted.
- Merge 4 and 2: 2 -> 4.
- Merge 1 and 3: 1 -> 3.
- Merge 2 -> 4 and 1 -> 3: take 1, then 2, then 3, then 4.

Result: 1 -> 2 -> 3 -> 4

3. Time Complexity

Time Complexity: O(n log n)

Each time I cut the list in half, so there are about log n levels. On each level, finding the middle and merging look at all n nodes together, which is O(n) work. So the total is n times log n. The recursion uses O(log n) extra memory for the call stack.

4. Reflection / Improvement

- Is there a more efficient approach? In time, no. O(n log n) is the best for sorting by comparing values. In memory, yes, a little.
- What would I need to change? I would use bottom-up merge sort. It merges lists of size 1, then 2, then 4, and so on, with loops instead of recursion.
- What complexity could the improved solution achieve? O(n log n) time and O(1) memory, instead of O(log n) memory for the stack.
