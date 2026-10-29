1. Problem

We get the root of a binary tree and need to return the values in postorder: first the whole left subtree, then the whole right subtree, and the node itself last.

2. Approach

The task asks for an iterative solution, so I use a stack. The idea is to go in the reverse order: node, then right, then left, and add every value to the front of the result list. Reading that backwards gives left, right, node, which is exactly postorder.

For this I take a node from the stack, add its value to the front of the result, and push its left child and then its right child (only if they exist). The right child is taken out of the stack first, so the right side is handled before the left side.

Example 1, tree [1,null,2,3]: stack is [1]. Take 1, result [1], push its right child 2. Take 2, result [2,1], push its left child 3. Take 3, result [3,2,1]. Done.

Example 2, tree [1,2,3,4,5,null,8,null,null,6,7,9]: take 1, push 2 then 3. Take 3, result [3,1], push 8. Take 8, result [8,3,1], push 9. Take 9, result [9,8,3,1]. Take 2, push 4 then 5. Take 5, push 6 then 7. Take 7, take 6, take 4. Every new value goes to the front, so the final result is [4,6,7,5,2,9,8,3,1].

Examples 3 and 4: an empty tree returns an empty list, a single node returns [1].

My first idea was to copy the preorder stack code, but that does not work, because in postorder a node must wait until both its children are finished, and I would need extra marks to know if the right side was already done. Reversing a "node, right, left" walk is much simpler. I also had to be careful with the order of pushing: if I push the right child first, I get "node, left, right" reversed, which is wrong.

3. Time Complexity

Time Complexity: O(n). Every node is pushed and popped once, and adding to the front of a LinkedList is O(1). Extra memory for the stack is O(h), where h is the height of the tree.

4. Reflection / Improvement

Time can't be better than O(n) because every value must be returned. Morris traversal can use O(1) extra memory, but it changes the tree links for a while and is harder to write, so for at most 100 nodes the stack is the better choice.
