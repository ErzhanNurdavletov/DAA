1. Problem

We get the root of a binary tree and need to add up the values of all left leaves. A leaf is a node with no children, and a left leaf is a leaf that is the left child of its parent.

2. Approach

I used recursion. A node can't know by itself if it is a left child, so I check it from the parent. At each node I look at its left child: if the left child exists and has no children, I add its value. If it has children, I go into it and continue there. Then I also go into the right child, because left leaves can be deeper on the right side. Null returns 0.

Example 1, tree [3,9,20,null,null,15,7]: at node 3 the left child is 9, it has no children, so I add 9. Then I go right to 20. Its left child is 15, a leaf, so I add 15. Its right child is 7, which is a leaf but a right one, so I go into it and it adds nothing. Total is 9 + 15 = 24.

Example 2, tree [1]: the root has no children at all, so the sum is 0. The root is a leaf, but it is not a left child of anything.

At first I just added up all leaves, which gives 9 + 15 + 7 = 31 for Example 1, because 7 is a right leaf and must not be counted. Then I tried to add any left child value, but a left child with its own children is not a leaf, so I must check that both of its sides are empty. I also noticed that the root alone must give 0, which works well when the check is done from the parent. Another option is to pass a flag "is this a left child" down the recursion, but checking from the parent is shorter.

3. Time Complexity

Time Complexity: O(n). Every node is visited once with constant work. Memory is O(h) for the recursion, where h is the height of the tree.

4. Reflection / Improvement

Time can't be better than O(n) because a left leaf can be anywhere in the tree, so every node must be checked. An iterative version with a stack or a queue would avoid recursion limits, but with at most 1000 nodes the recursive one is fine.
