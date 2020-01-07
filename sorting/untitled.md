# 280. Wiggle Sort \(easy\)

## Question:

Given an unsorted array nums, reorder it in-place such that nums\[0\] &lt;= nums\[1\] &gt;= nums\[2\] &lt;= nums\[3\]…

Example:

Input: nums = \[3,5,2,1,6,4\] Output: One possible answer is \[3,5,1,6,2,4\]

## Thought:

If numbers at odd indices are smaller than their next number, we swap them. And if numbers at even indices are bigger than their next number, we swap them.

## Solution:

```text
class Solution:
    def wiggleSort(self, nums):
        for i in range(len(nums)-1): # get ride of stepping out of index
            if i % 2 == 0 and nums[i] > nums[i+1]:
                nums[i], nums[i+1] = nums[i+1], nums[i]
            elif i % 2 == 1 and nums[i] < nums[i+1]:
                nums[i], nums[i+1] = nums[i+1], nums[i]
```

