1. Problem

We get the root of a binary tree and need to return the values in preorder: first the node itself, then the whole left subtree, then the whole right subtree.

2. Approach

The task asks for an iterative solution, so I use a stack instead of recursion. I put the root on the stack. Then, while the stack is not empty, I take the top node, write its value to the result, and push its right child and then its left child (only if they exist). Because the stack gives back the last thing I put in, the left child comes out first, so the left side is always done before the right side.

Example 1, tree [1,null,2,3]: stack is [1]. Take 1, result [1], push its right child 2. Take 2, result [1,2], push its left child 3. Take 3, result [1,2,3]. Stack is empty, done.

Example 2, tree [1,2,3,4,5,null,8,null,null,6,7,9]: take 1, push 3 then 2. Take 2, push 5 then 4. Take 4 (no children). Take 5, push 7 then 6. Take 6, take 7. Take 3, push 8. Take 8, push 9. Take 9. Result is [1,2,4,5,6,7,3,8,9].

Examples 3 and 4: an empty tree returns an empty list, a single node returns just [1].

At first I pushed the left child before the right one. That gives the right subtree first, which is the wrong order, because the stack reverses things. So the right child must go in first. I also forgot to check for null before pushing, which crashes on leaves. The recursive solution is simple (add value, go left, go right), but I used the stack as the follow up asks.

3. Time Complexity

Time Complexity: O(n). Every node is pushed and popped exactly once. Memory is O(h) for the stack, where h is the height of the tree, and O(n) in the worst case for a one-sided tree.

4. Reflection / Improvement

Time can't be better than O(n) because every value must be returned. Less memory is possible with Morris traversal, which needs O(1) extra space, but it temporarily changes the tree links and is harder to write, so for at most 100 nodes the stack is the better choice.
