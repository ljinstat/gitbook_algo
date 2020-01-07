# 32（一）：不分行从上往下打印二叉树

## Question:

从上往下打印出二叉树的每个结点，同一层的结点按照从左到右的顺序打印。 

## Thought:

* 迭代：BFS level那一部分，用队列，因为是FIFO，所以可以从左到右打印。
* 递归：DFS 刚开始自己想，想不清楚
* 利用队列实现BFS，同样可以运用到有向图上。树是图的退化形式。

## Solution:

```text
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        # bfs
        result = []
        if not root:
            return result
        dq = collections.deque([root])
        while dq:
            curr = dq.popleft()
            if curr.left:
                dq.append(curr.left)
            if curr.right:
                dq.append(curr.right)
        return result
        # dfs---------------------
        result = []
        self.dfs(root, result)
        return result
        
    def dfs(self, root, result):
        if root:
            result.append(root.val)
            self.dfs(root.left, result)
            self.dfs(root.right, result)
```

