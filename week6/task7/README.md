1. Problem

We get the root of a binary tree and need to flip it like in a mirror: at every node the left and right children change places. We return the same root.

2. Approach

I used recursion. For the current node I swap its left and right child with a temporary variable. Then I do the same for the new left child and the new right child. An empty node (null) is the stopping point, and at the end I return the root.

Example 2, tree [2,1,3]: at node 2 I swap 1 and 3, so the left child is 3 and the right child is 1. Then I go into 3 and 1, they have no children, so nothing changes. Result is [2,3,1].

Example 1, tree [4,2,7,1,3,6,9]: at 4 I swap 2 and 7. Then at 7 (now on the left) I swap 6 and 9. At 2 (now on the right) I swap 1 and 3. Result is [4,7,2,9,6,3,1].

Example 3: the tree is empty, so I return null.

At first I thought it is enough to swap the children only at the root, but then the inside of each subtree stays the same, so the tree is not really mirrored. The swap must happen at every node. I also made the mistake of writing left = right and then right = left without a temporary variable, which makes both sides the same node and loses one subtree. The order does not matter: I can swap first and recurse after, or recurse first and swap after. I also thought about a BFS with a queue, which works too, but recursion is shorter and the depth is at most 100.

3. Time Complexity

Time Complexity: O(n). Every node is visited once and the swap takes constant time. Memory is O(h) for the recursion, where h is the height of the tree.

4. Reflection / Improvement

Time can't be better than O(n) because every node has to be changed. If the tree was very deep, I would use an iterative version with a queue or a stack to avoid a stack overflow, but the time would stay O(n).
