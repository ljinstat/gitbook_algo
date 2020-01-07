# 596 Minimum Subtree \(lintcode\)

## Question:

**Description**  
Given a binary tree, find the subtree with minimum sum. Return the root of the subtree.  
  
**Notice**  
LintCode will print the subtree which root is your return node.  
It's guaranteed that there is only one subtree with minimum sum and the given binary tree is not an empty tree.  
  
  
**Example**  
Given a binary tree:  
  
      1  
    /   \  
 -5      2  
 / \     /  \  
0   2 -4  -5  
return the node 1.

## Thought:

* divide conquer + traverse

## Solution:

```text
class Solution(object):
    def findSubtree(self, root):
        subtree = None
        subtreeSum = sys.maxsize
        self.helper(root, subtree, subtreeSum)
        return subtree
    
    def helper(self, root, subtree, subtreeSum):
        if not root:
            return 0
        # divide and conquer
        sum = self.helper(root.left) + self.helper(root.right) + root.val
        # traverse 打擂台
        if sum < subtreeSum:
            subtreeSum = sum
            subtree = root
        return sum
```

