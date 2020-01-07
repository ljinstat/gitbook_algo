# 28：对称的二叉树 （101）

## Question:

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

## Thought:

* iteration: O\(n\), O\(n\)
* recursion: O\(n\), O\(n\) \(stack\)

## Solution:

```text
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        # recursion
        return self.isMirror(root, root)
    
    def isMirror(self, left, right):
        if not left and not right:
            return True
        if not left or not right:
            return False
        if left.val == right.val:
            return self.isMirror(left.left, right.right) and \
                   self.isMirror(left.right, right.left)
        else:
            return False
        # iteration
        if not root:
            return True
        dq = collections.deque([(root.left, root.right), ])
        while dq:
            left, right = dq.popleft()
            if not left and not right:
                continue
            if not left or not right:
                return False
            if left.val != right.val:
                return False
            else:
                dq.append((left.left, right.right))
                dq.append((left.right, right.left))
        return True
```

