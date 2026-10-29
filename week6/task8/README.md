1. Problem

We get the root of a binary tree and need to return every path from the root to a leaf as a string like "1->2->5". A leaf is a node with no children. The order of paths does not matter.

2. Approach

I used recursion (DFS) and carry the path built so far as a string. At each node I add its value to the string. If the node is a leaf, the path is finished and I add it to the result. If not, I add "->" to the string and continue to the left and right child.

Example 1, tree [1,2,3,null,5]: I start at 1 with the path "1->". Going left to 2, the path is "1->2->". Node 2 has no left child, and its right child is 5. At 5 the path becomes "1->2->5", it is a leaf, so I save it. Back at 1, I go right to 3, the path is "1->3", it is a leaf, so I save it. Result is ["1->2->5","1->3"].

Example 2: the tree is just [1], the root is a leaf, so the result is ["1"].

My first mistake was to save the path when I reach a null child. That is wrong, because node 2 has one empty side, and it would save "1->2" even though 2 is not a leaf. So the leaf check must be done on the node itself, when both children are empty. Another idea was to use one StringBuilder and remove the last part when going back, which works, but it is easy to forget to undo it. Strings can't be changed, so every call has its own copy and I don't need to go back.

3. Time Complexity

Time Complexity: O(n * h), where n is the number of nodes and h is the height of the tree. Each node is visited once, but building the path string takes time up to the length of the path. In the worst case, for a long one-sided tree, this is O(n^2).

4. Reflection / Improvement

A StringBuilder with going back would avoid copying the string at each node, but the result strings still have to be written out, so the worst case stays about the same. With at most 100 nodes the simple version is good enough.
