# README.md

## 1. Problem

Traverse a binary tree in **Inorder** sequence (Left subtree → Root → Right subtree) and return a list of all node values.

## 2. Approach

Uses a recursive Depth-First Search (DFS) strategy.

1. Recursively traverse the left subtree.
2. Store the current node's value in the result list.
3. Recursively traverse the right subtree.

### Example Walkthrough (`root = [1, null, 2, 3]`)

1. Start at `1`: left is `null` → add `1` (`[1]`) → go right to `2`.
2. At `2`: go left to `3`.
3. At `3`: left is `null` → add `3` (`[1, 3]`) → right is `null`.
4. Back to `2`: add `2` (`[1, 3, 2]`) → right is `null`.
5. Result: `[1, 3, 2]`.

### Challenges

Missing the base check (`node == null`) causes a null pointer error. Swapping execution order breaks the required Inorder sequence.

## 3. Time Complexity

* **Time Complexity:** $O(n)$, where $n$ is the total number of nodes (each node is visited once).
* **Space Complexity:** $O(h)$, where $h$ is the height of the tree (recursion call stack memory). Worst case $O(n)$, best case $O(\log n)$.

## 4. Reflection / Improvement

* **More Efficient Approach:** Morris Traversal.
* **Changes Needed:** Dynamically modify tree links to create temporary pointers back to parent nodes, removing the need for call stack frames.
* **Achievable Complexity:** Time complexity remains $O(n)$, while extra space drops to $O(1)$.