1. Problem

We get two binary trees and need to put them on top of each other and make one new tree. Where two nodes are on the same place, the new node has the sum of their values. Where only one tree has a node, that node is used as it is.

2. Approach

I used recursion and walk through both trees at the same time. If one of the two nodes is null, I return the other one, because there is nothing to add (if both are null, this returns null). If both nodes exist, I make a new node with the sum of the values, then merge the left children for its left side and the right children for its right side.

Example 2, trees [1] and [1,2]: both roots exist, so the new root is 1 + 1 = 2. For the left side, the first tree has nothing and the second tree has node 2, so I take node 2. On the right side both are empty, so it stays null. Result is [2,2].

Example 1, trees [1,3,2,5] and [2,1,3,null,4,null,7]: the roots give 1 + 2 = 3. On the left, 3 + 1 = 4. Under it, the left side has 5 in the first tree and nothing in the second, so I take 5. The right side has nothing in the first tree and 4 in the second, so I take 4. Back on the root's right side, 2 + 3 = 5. Its left side is empty in both trees, so null, and its right side takes 7 from the second tree. Result is [3,4,5,5,4,null,7].

At first I wanted to change the first tree directly and add the values into it. That does not work when the first tree has no node in some place, because there is nothing to attach the value to, and it also destroys the input. Another mistake I made was returning null as soon as one of the nodes was null, which loses the whole part that exists in the other tree. The check for null must come before I read any value, otherwise I get a crash.

3. Time Complexity

Time Complexity: O(min(n, m)), where n and m are the sizes of the two trees. I only go deeper while both nodes exist, and when one is null I return the other subtree right away without visiting it. Memory is O(h) for the recursion, where h is the height of the smaller overlap.

4. Reflection / Improvement

Time can't really be better, because every overlapping node needs one addition. One small point: when one side is null I reuse the existing subtree of the other tree instead of copying it, which is faster, but it means the new tree shares some nodes with the input. If separate copies were needed, I would copy those subtrees, and the time would become O(n + m).
