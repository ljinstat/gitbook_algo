# 42：连续子数组的最大和 \(53\)

## Question:

输入一个整型数组，数组里有正数也有负数。数组中一个或连续的多个整数组成一个子数组。求所有子数组的和的最大值。要求时间复杂度为O\(n\)。

## Thought:

* dynamic programming: 通过对比curr\_sum和sum，先求当前sum的最大值，然后再对比curr\_sum和max\_sum。
* 举例子找到规律 divide and conquer：一样的思路，只是写法不一样。
* assumption: positive and negative numbers? sorted? null/ empty: return 0? complexity: O\(n\)

## Solution:

```text
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        # example
        if not nums or len(nums) == 0:
            return 
        curr_sum = 0
        max_sum = - sys.maxint
        for num in nums:
            if curr_sum > 0:
                curr_sum += num
            else:
                curr_sum = num
            if curr_sum > max_sum:
                max_sum = curr_sum
        return max_sum
        # dynamic programming
        curr_sum = nums[0]
        max_sum = nums[0]
        for num in nums[1:]:
            curr_sum = max(curr_sum + num, num)
            max_sum = max(curr_sum, max_sum)
        return max_sum
```

