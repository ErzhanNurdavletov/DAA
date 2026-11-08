README Report: Palindrome Linked List

1. Problem

I get a linked list. I need to check if it reads the same from left to right and from right to left.

2. Approach

In a singly linked list I cannot go backwards. So I reverse the second half of the list and compare it with the first half.

Steps:
- Find the middle. One pointer moves 1 step, another moves 2 steps. When the fast one reaches the end, the slow one is at the end of the first half.
- Reverse the second half of the list.
- Compare the first half with the reversed second half, node by node. If I find different values, the answer is false. If everything is equal, the answer is true.

For odd length, the middle node is not compared. It is always equal to itself.

Example 1: 1 -> 2 -> 2 -> 1
- The middle is the first 2. First half: 1, 2. Second half: 2, 1.
- I reverse the second half: 1, 2.
- Compare 1 with 1: equal. Compare 2 with 2: equal.
- Answer: true.

Example 2: 1 -> 2
- First half: 1. Second half: 2.
- Compare 1 with 2: not equal.
- Answer: false.

3. Time Complexity

Time Complexity: O(n)

I go through the list three times: to find the middle, to reverse the second half, and to compare. Each pass is at most n steps, so the total is still O(n). I use only a few pointers, so extra memory is O(1).

4. Reflection / Improvement

- Is there a more efficient approach? Not in time, because we must read every node. A simpler way is to copy values into an ArrayList and compare both ends. It is also O(n) time, but it uses O(n) memory.
- What would I need to change? My solution already uses less memory. A small improvement is to reverse the second half back after the check, so the input list is not changed.
- What complexity could the improved solution achieve? O(n) time and O(1) memory. This is what my solution has.
