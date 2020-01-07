# 7：重建二叉树 \(105\)

## Question:

输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1, 2, 4, 7, 3, 5, 6, 8}和中序遍历序列{4, 7, 2, 1, 5, 3, 8, 6}，则重建出二叉树并输出它的根结点。

## Thought:

* preorder的第一个节点是root，而inorder的root在中间，root的左边是左树，右边是右树。利用preorder找到inorder中子树的root，并找到左右节点。
* 用 Hash Map 提高检索速度。
* [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/discuss/34579/Python-short-recursive-solution.](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/discuss/34579/Python-short-recursive-solution.)
* \(a\) Inorder \(Left, Root, Right\) 
* \(b\) Preorder \(Root, Left, Right\) 
* \(c\) Postorder \(Left, Right, Root\)

## Solution:

```text
class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: TreeNode
        """
        if inorder:
            idx = inorder.index(preorder.pop(0)) #??
            root = TreeNode(inorder[idx])
            root.left = self.buildTree(preorder, inorder[:idx])
            root.right = self.buildTree(preorder, inorder[idx+1:])
            return root
        # ------------------------------------
        # hashmap faster
        inorder_dict = {}
        for i, num in enumerate(inorder):
            inorder_dict[num] = i
        
        def helper(start, end):
            if start < end:
                root = TreeNode(preorder.pop(0))
                idx = inorder_dict[root.val]
                root.left = helper(start, idx)
                root.right = helper(idx+1, end)
                return root
            
        return helper(0, len(inorder))
```

