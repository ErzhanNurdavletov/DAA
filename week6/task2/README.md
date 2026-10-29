1. Problem

We get the root of a binary tree and need to find how many nodes are on the longest path from the root down to a leaf. An empty tree gives 0.

2. Approach

I solved it with recursion. The depth of a node is 1 plus the bigger depth of its left and right children. A missing child (null) has depth 0, so that is where the recursion stops.

Example 1, tree [3,9,20,null,null,15,7]: node 9 has no children, so its depth is 1 + max(0,0) = 1. Nodes 15 and 7 are also leaves, so each is 1. Node 20 then gets 1 + max(1,1) = 2. The root 3 gets 1 + max(1,2) = 3.

Example 2, tree [1,null,2]: node 2 is a leaf, so it is 1. Node 1 has no left child (0) and the right is 1, so the answer is 1 + max(0,1) = 2.

At first I returned 0 for a leaf and counted edges, which gave answers that were one too small, because the task counts nodes. I also tried checking only for leaves as the base case, but it gets messy with nodes that have just one child and breaks on an empty tree. Using null as the base case fixed both problems. I also thought about BFS with a queue, which works too, but the recursive version is shorter and follows the definition directly.

3. Time Complexity

Time Complexity: O(n). Every node is visited once and the work per node is constant. Extra memory is O(h) for the recursion stack, where h is the height of the tree.

4. Reflection / Improvement

Time can't get better than O(n), since every node has to be checked. The only thing I would change is making it iterative (BFS or DFS with a stack) to avoid a stack overflow on a very deep, one-sided tree. The time stays O(n).
