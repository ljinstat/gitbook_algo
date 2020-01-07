# Two sum - closest to target

## Quesiton:

Given an int array `nums` and an int `target`. Find two integers in `nums` such that the sum is closest to `target`.

## Thought:

* sorted + two pointers
* return two integers
* return diff

## Solution:

```text
class Solution:
    def twoSum(self, nums, target):
        if not nums or len(nums) == 0:
            return []
        result = [0, 0]
        nums = sorted(nums)
        left = 0
        right = len(nums) - 1
        minDiff = sys.maxsize
        while left < right:
            diff = abs(nums[right] + nums[left] - target)
            curr = nums[right] + nums[left]
            if diff < minDiff:
                result[0] = nums[left]
                result[1] = nums[right]
                minDiff = diff
            if curr > target:
                right -= 1
            elif curr < target:
                left += 1
        return result
        
```

### 

