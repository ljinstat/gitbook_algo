# 33：二叉搜索树的后序遍历序列

## Question:

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则返回true，否则返回false。假设输入的数组的任意两个数字都互不相同。**BST的后序序列的合法序列是，对于一个序列S，最后一个元素是x （也就是根），如果去掉最后一个元素的序列为T，那么T满足：T可以分成两段，前一段（左子树）小于x，后一段（右子树）大于x，且这两段（子树）都是合法的后序序列。**

## Thought:

* 递归：先把最后一个节点当做根节点，找到左子树跟右子树。左子树的值都要比根节点小，右子树的值都要比根节点大。然后再判断左子树和右子树是否是二叉搜索树的后序遍历序列。
* 33.2 和 7 题， 有类似的解法

## Solution：

```text
class Solution(object):
    def verifyPostBST(self, sequence):
        if not sequence or len(sequence) == 0:
            return False
        root = sequence[-1]
        # find left tree
        for i in range(len(sequence)):
            if sequence[i] > root:
                break
        # find right tree
        for j in range(i, len(sequence)-1):
            if sequence[j] < root:
                return False
        left = self.verifyPostBST(sequence[:i])
        right = self.verifyPostBST(sequence[i:-1])
        return left and right
```



