# 32（三）：之字形打印二叉树 \(103\)

## Question:

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

## Thought:

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
        flag = True
        dq = collections.deque([root])
        while dq:
            curr_level, size = [], len(dq)
            for i in range(size):
                curr = dq.popleft()
                if curr.left:
                    dq.append(curr.left)
                if curr.right:
                    dq.append(curr.right)
                if flag:
                    curr_level.append(curr.val)
                else:
                    curr_level.insert(0, curr.val) # insert number in front
            result.append(curr_level)
            flag = !flag
        return result
        # dfs
        result = []
        self.dfs(root, 0, result)
        return result
        
    def dfs(self, root, level, result):
        if root:
            if len(result) < level+1:
                result.append([])
            if level & 1 == 0: # even
                result[level].append(root.val)
            else:
                result[level].insert(0, root.val)
            self.dfs(root.left, level+1, result)
            self.dfs(root.right, level+1, result)
```

