# Two sum - difference equals to target

## Quesiton:

Given an array of integers, find two numbers that their difference equals to a target value. where index1 must be less than index2. Please note that your returned answers \(both index1 and index2\) are NOT zero-based.

Given nums = \[2, 7, 15, 24\], target = 5 return \[1, 2\] \(7 - 2 = 5\)

## Thought:

* first turn the right point to the point where the difference is no less than target
* then move the left point

## Solution:

```text
class Solution:
    def twoSum(self, nums, target):
        if not nums or len(sums) == 0:
            return []
        result = [0, 0]
        right = 0
        for left in range(len(nums)):
            if nums[right] - nums[left] == target:
                result[0] = left
                result[1] = right
            if right < len(nums) - 1 and left == right:
                right += 1
            while right < len(nums) - 1 and nums[right] - nums[left] < target:
                right += 1
        return result
```

