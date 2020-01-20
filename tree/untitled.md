# 236. Lowest Common Ancestor of a Binary Tree \(medium\)

## Question:

Given a binary tree, find the lowest common ancestor \(LCA\) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants \(where we allow **a node to be a descendant of itself**\).”

Given the following binary tree:  root = \[3,5,1,6,2,0,8,null,null,7,4\]

## Thought:

* **recursion: put self.result in \_\_init\_\_ \(\*\*\*\)**
* divide and conquer, not traverse
* iteration 
* what if we have parent in treenode class? first parent in common
* **p, q are both in the same side, return left or right; p, q are from two sides, it means that root is LCA**
* The least common ancestor would then be the node for which both the subtree recursions return a `True` flag. It can also be the node which itself is one of `p` or `q` and for which one of the subtree recursions returns a `True` flag.
*  1. Start traversing the tree from the root node.
  2. If the current node itself is one of `p` or `q`, we would mark a variable `mid` as `True` and continue the search for the other node in the left and right branches.
  3. If either of the left or the right branch returns `True`, this means one of the two nodes was found below.
  4. If at any point in the traversal, any two of the three flags `left`, `right` or `mid` become `True`, this means we have found the lowest common ancestor for the nodes `p` and `q`.

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
        # 1. brief way------------------------
        # if the current node is one of the target nodes
        mid = node == p or node == q
        # if any two of the three flags are True
        if right + left + mid >= 2:
            self.result = node
        return left or right or mid
        # 2. clear way-----cannot work--------------------
        #if left and right:
        #    return node
        #if left:
        #    return left
        #if right:
        #    return right
        #return None
```

