1. Problem

Find the shortest way from the root of a tree down to a leaf, counted in nodes. A leaf is a node with no children.

2. Approach

I go through the tree level by level with a queue. The first node without children is the closest leaf, so I stop and return its level.

Example 1: level 1 is node 3, it has children. Level 2 starts with node 9, it has no children, so the answer is 2.

Example 2: every node has just one child, so I go down until node 6 on level 5. Answer is 5.

I first tried 1 + min(left, right) like in max depth. It is wrong when a node has only one child, because the empty side counts as 0 and the node looks like a leaf. For Example 2 it gives 1 instead of 5. Recursion that fixes this also works, but a long one-sided tree can overflow the stack, so I used BFS.

3. Time Complexity

Time Complexity: O(n). In the worst case I visit each node once.

4. Reflection / Improvement

Better than O(n) is not possible in the worst case. BFS is already good because it stops at the first leaf.
