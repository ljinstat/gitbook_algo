# 32（二）：分行从上往下打印二叉树 \(102\)

## Question:

从上往下打印出二叉树的每个结点，同一层的结点按照从左到右的顺序打印。 也就是二叉树的层序遍历

## Thought:

* 迭代：BFS level那一部分，怎么确定要打印几个呢？这要想清楚
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
        # bfs------------------------
        result = []
        if not root:
            return result
        dq = collections.deque([root])
        while dq:
            curr_level, size = [], len(dq) # size of nodes at one level
            for _ in range(size):
                curr = dq.popleft()
                if curr.left:
                    dq.append(curr.left)
                if curr.right:
                    dq.append(curr.right)
                curr_level.append(curr.val)
            result.append(curr_level)
        return result
        # dfs---------------------------
        result = []
        self.dfs(root, 0, result)
        return result
        
    def dfs(self, root, level, result):
        if root:
            if len(result) < level+1:
                result.append([])
            result[level].append(root.val)
            self.dfs(root.left, level+1, result)
            self.dfs(root.right, level+1, result)
```

