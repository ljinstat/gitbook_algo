# 11：旋转数组的最小数字 \(153，154 重复数字\)

## Question:

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如数组{3, 4, 5, 1, 2}为{1, 2, 3, 4, 5}的一个旋转，该数组的最小值为1。

## Thought:

* binary search
* 时间复杂度：O\(logN\)
* 有没有相同的数字？
* left + \(right - left\) / 2 不会溢出，但是直接相加可能溢出

## Solution:

```text
class Solution(object):
    def findMin(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 
        if len(nums) == 1:
            return nums[0]
        left = 0
        right = len(nums) - 1
        # no rotation
        if nums[right] > nums[0]:
            return nums[0]
        while left <= right:
            mid = left + (right - left) / 2
            # condition of returning
            if nums[mid] < nums[mid - 1]:
                return nums[mid]
            if nums[mid] > nums[mid + 1]:
                return nums[mid + 1]
            # condition of changing index
            if nums[mid] < nums[0]:
                right = mid - 1
            else:
                left = mid + 1
```

