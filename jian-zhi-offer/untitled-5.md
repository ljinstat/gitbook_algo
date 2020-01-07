# 66. 构建乘积数组 \(238\)

## Question:

给定一个数组A\[0, 1, …, n-1\]，请构建一个数组B\[0, 1, …, n-1\]，其中B中的元素B\[i\] =A\[0\]×A\[1\]×… ×A\[i-1\]×A\[i+1\]×…×A\[n-1\]。不能使用除法。

## Thought:

* 把index i的元素的左边和右边的数值连乘，避开index i
* 不用到多余空间的方法，想起来要注意怎么乘右边的数值。
* 方法一：用一个array做例子，左边就是只考虑从index 1开始的数，下一个left是前一个left的值乘以前一个数。
* 方法二：直接先算左边的作为result，乘以右边（一个数），再用当前的数乘以右边更新右边。

## Solution:

```text
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        # left and right product lists
        length = len(nums)
        left, right, result = [0]*length, [0]*length, [0]*length
        left[0] = 1
        for i in range(1, length):
            left[i] = left[i-1] * nums[i-1]
        right[length-1] = 1
        for i in range(length-2, -1, -1):
            right[i] = right[i+1] * nums[i+1]
        for i in range(length):
            result[i] = left[i] * right[i]
        return result
        # O(1) space approach
        length = len(nums)
        right, result = 1, [0]*length
        result[0] = 1
        for i in range(1, length):
            result[i] = result[i-1] * nums[i-1]
        for i in range(length-1, -1, -1):
            result[i] = result[i] * right # from last element, multiply the left and the right
            right *= nums[i] # update right
        return result
```

