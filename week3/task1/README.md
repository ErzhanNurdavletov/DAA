README Report: Merge Two Sorted Lists

1. Problem

I get two sorted linked lists. I need to join them into one sorted list and return it. The new list is made from the nodes of the two given lists.

2. Approach

I add a dummy node at the start, and a pointer called tail that always stands at the end of the new list.

- I compare the first nodes of both lists.
- The smaller node I attach to the end of the new list, and I move forward in the list I took it from.
- I repeat this until one list ends.
- Then I attach the rest of the other list. It is already sorted, so I do not need to check it.
- At the end I return the node after dummy. This is the real head.

Example: list1 = 1 -> 2 -> 4 and list2 = 1 -> 3 -> 4
- Compare 1 and 1. Take the one from list1. New list: 1.
- Compare 2 and 1. Take 1 from list2. New list: 1 -> 1.
- Compare 2 and 3. Take 2. New list: 1 -> 1 -> 2.
- Compare 4 and 3. Take 3. New list: 1 -> 1 -> 2 -> 3.
- Compare 4 and 4. Take the one from list1. New list: 1 -> 1 -> 2 -> 3 -> 4.
- list1 ended. I attach the rest of list2, which is 4.

Result: 1 -> 1 -> 2 -> 3 -> 4 -> 4

Special case: if one list is empty, I just attach the other list, and the result is that list.

3. Time Complexity

Time Complexity: O(m + n)

In every step I take one node from one of the lists, and I never go back. So the number of steps is not more than the total number of nodes, which is m + n. I reuse the old nodes and use only a few pointers, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? Not in time. We must look at every node, so O(m + n) is the minimum.
- What would I need to change? Nothing, because the solution already reuses the nodes. A recursive solution is shorter, but it uses O(m + n) stack memory, so it is worse. Making a new list with new nodes would use O(m + n) memory too.
- What complexity could the improved solution achieve? O(m + n) time and O(1) memory. This is what my solution has.
