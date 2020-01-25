# 236. Lowest Common Ancestor of a Binary Tree \(medium\)

## Question:

Given a binary tree, find the lowest common ancestor \(LCA\) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants \(where we allow **a node to be a descendant of itself**\).”

Given the following binary tree:  root = \[3,5,1,6,2,0,8,null,null,7,4\]

## Thought:

* recursion: put self.result in \_\_init\_\_
* divide and conquer, not traverse
* iteration 
* what if we have parent in treenode class? first parent in common
* **p, q are both in the same side, return left or right; p, q are from two sides, it means that root is LCA**

## Solution:

```text
class Solution:
    def __init__(self):
        self.result = None
        
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if not root:
            return False
        self.recursion(root, p, q)
        return self.result
    
        # recursion
    def recursion(self, node, p, q):
        if not node:
            return False
        left = self.recursion(node.left, p, q)
        right = self.recursion(node.right, p, q)
        # 1. brief way
        mid = node == p or node == q
        if right + left + mid >= 2:
            self.result = node
        return left or right or mid
        # 2. clear way
        if left and right:
            return node
        if left:
            return left
        if right:
            return right
        return None
```

