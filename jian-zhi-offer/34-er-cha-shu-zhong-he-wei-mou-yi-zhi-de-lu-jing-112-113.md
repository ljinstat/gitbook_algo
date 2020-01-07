# 34：二叉树中和为某一值的路径 \(112, 113\)

## Question:

输入一棵二叉树和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。

## Thought:

* 递归
* DFS + stack from leaf to root
* assumption: input: node; output: boolean or arrays; null/empty: return False or None

## Solution:

```text
class Solution(object):
    # find whether there exits sums of paths equal to sum 
    def pathSum(self, root, sum):
        # recursion
        if not root:
            return False
        if not root.left and not root.right and sum - root.val == 0:
            return True
        sum -= root.val
        return self.pathSum(root.left, sum) or self.pathSum(root.right, sum)
    
    # find all valid paths --> preoder --> path - leaf --> right then left
    def pathSum2(self, root, sum):
        # dfs + stack
        if not root:
            return []
        stack = [(root, sum-root.val, [root.val])]
        result = []
        while stack:
            curr, residu, ls = stack.pop()
            if not curr.left and not curr.right and residu == 0:
                result.append(ls)
            if curr.right:
                self.pathSum2(curr.right, residu-curr.right.val, ls+[curr.right.val])
            if curr.left:
                self.pathSum2(curr.left, residu-curr.left.val, ls+[curr.left.val])
        return result
```

