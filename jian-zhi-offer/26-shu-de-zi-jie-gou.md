# 26：树的子结构 \(572\)

## Question:

输入两棵二叉树A和B，判断B是不是A的子结构。（约定空树不是任意一个树的子结构）

## Thought:

* recursion, iteration
* 空值的处理
* 有两部分，一个是找到两个相等节点，判断子树是否在全树里面；二是找到子树，确认有子树的存在。
* 测试用例：树A和树B的头结点有一个或者两个是空的；树的所有节点都只有左侧或者右侧；节点中含有分叉。
* **判断两个小数是否相等，只能判断它们的差的绝对值是否在一个很小的范围内。** 
* 防御性编程：判断无效输入。
* **树的对比：当要对比两个树的node时，用迭代遍历左子树和右子树的每个node。**

## Solution:

```text
class Solution(object):
    def isSubtree(self, s, t):
        """
        :type s: TreeNode
        :type t: TreeNode
        :rtype: bool
        """
        if not s:
            return False
        if self.isMatch(s, t):
            return True
        return self.isSubtree(s.left, t) or self.isSubtree(s.right, t)
    
    def isMatch(self, s, t):
        if not s and not t:
            return True
        if not s or not t:
            return False
        if s.val != t.val:
            return False
        # traverse the subtree till the end
        return self.isMatch(s.left, t.left) and self.isMatch(s.right, t.right)

```

