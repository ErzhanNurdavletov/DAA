1. Problem

We get a binary tree and a number targetSum. We need to say if there is a path from the root down to a leaf where the values add up to targetSum. A leaf is a node with no children.

2. Approach

I used recursion. At each node I subtract its value from the target and ask the same question for the left and right child with the smaller target. If the node is a leaf, I just check if its value equals what is left. If one of the sides gives true, the answer is true.

Example 1, target 22: from 5 the target becomes 17, from 4 it becomes 13, from 11 it becomes 2. Node 11 has children 7 and 2. Node 7 is a leaf but 7 is not 2, so false. Node 2 is a leaf and 2 equals 2, so true. The path is 5, 4, 11, 2.

Example 2, tree [1,2,3], target 5: the leaves are 2 and 3, with paths 1+2=3 and 1+3=4. Neither is 5, so false.

Example 3: the tree is empty, so there is no path and the answer is false, even when the target is 0.

At first I checked "target is 0" when I reach a null child. That is wrong: for tree [1,2] and target 1, node 1 has no right child, so null gives 0 and the code says true, but 1 is not a leaf there. Checking at a real leaf node fixes it. Also, the values can be negative, so I can't stop early when the sum gets too big.

3. Time Complexity

Time Complexity: O(n). Every node is visited at most once with constant work. Memory is O(h) for the recursion, where h is the tree height.

4. Reflection / Improvement

Better than O(n) is not possible in the worst case, because any node can be on the right path. An iterative version with a stack would remove the recursion limit, but with up to 5000 nodes recursion is fine.
