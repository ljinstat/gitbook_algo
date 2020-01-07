# 27：二叉树的镜像 \(226\)

## Question:

请完成一个函数，输入一个二叉树，该函数输出它的镜像。

## Thought:

* recursion \(O\(n\), O\(h\)\) and iteration \(O\(n\), O\(n\)\)
* **画图简化思考**

## Solution:

```text
class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        # recursion
        if not root:
            return root
        # buttom up --------------------
        left = self.invertTree(root.left) # to the left child
        right = self.invertTree(root.right) # to the right child
        root.left, root.right = right, left # swap
        return root
        # top down ----------------------
        root.left, root.right = root.right, root.left
        if root.left:
            self.invertTree(root.left)
        if root.right:
            self.invertTree(root.right)
        return root
        # iteration ---------------------
        if not root:
            return root
        dq = collections.deque([root,])
        while dq:
            node = dq.popleft()
            if node:
                node.left, node.right = node.right, node.left
                dq.append(node.left)
                dq.append(node.right)
        return root
```

