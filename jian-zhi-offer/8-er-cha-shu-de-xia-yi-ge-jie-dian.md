# 8：二叉树的下一个结点

## Question:

树中的结点除了有两个分别指向左右子结点的指针以外，还有一个指向父结点的指针。给定一棵二叉树和其中的一个结点，如何找出中序遍历顺序的下一个结点？

## Thought:

* 如果一个节点有右子树，下一个节点就是右子树的最左子节点。从右子节点出发，一直沿着指向左子节点的指针，就能找到下一个节点。
* 如果一个节点没有右子树，且是父节点的左子节点，那下一个节点就是父节点。
* 如果一个节点没有右子树，且是父节点的右子节点，沿着指向父节点的指针向上遍历，直到找到一个它父节点\(父节点的父节点\)的左子节点的节点。如果这样的节点存在，这个节点的父节点就是我们要找的下一个节点。要是不存在，那么这个节点就没有下一个节点。
* 1. 看有没有右子树 2. 看是父节点的左还是右节点。

## Solution:

```text
 class Solution(object):
     def getNextnode(self, node):
         if not node:
             return None
         if node.right: # it has the right subtree
             node = node.right
             while node.left:
                 node = node.left
             return node
         else:
             while node.next:
                 if node == node.next.left: # left node of parent
                     return node.next
                 node = node.next
             return None
```

