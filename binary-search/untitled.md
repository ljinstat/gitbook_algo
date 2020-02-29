# 34. Find First and Last Position of Element in Sorted Array \(medium\)

## Question:

Given an array of integers `nums` sorted in ascending order, find the starting and ending position of a given `target` value.

Your algorithm's runtime complexity must be in the order of _O_\(log _n_\).

If the target is not found in the array, return `[-1, -1]`.

**Example 1:**

```text
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```

## Thought:

* two binary searches
* template: 
* while start + 1 &lt; end:
* mid = start + \(end - start\) // 2
* pay attention when copying the first part to the second part, don't copy results = \[\]

## Solution:

```text
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if not nums or len(nums) == 0: # Don't write not target
            return [-1, -1]
        result = []
        start = 0
        end = len(nums) - 1
        # first element 
        while start + 1 < end: # when we want to find an interval
            mid = start + (end - start) // 2
            if nums[mid] == target:
                end = mid # for first position, the first position must before end
            if nums[mid] > target:
                end = mid - 1
            if nums[mid] < target:
                start = mid + 1
        if nums[start] == target:
            result.append(start)
        elif nums[end] == target:
            result.append(end)
        else:
            result.append(-1)
        # last element 
        start = 0
        end = len(nums) - 1
        while start + 1 < end:
            mid = start + (end - start) // 2
            if nums[mid] == target:
                start = mid # for last position
            if nums[mid] > target:
                end = mid - 1
            if nums[mid] < target:
                start = mid + 1
        if nums[end] == target:
            result.append(end)
        elif nums[start] == target:
            result.append(start)
        else:
            result.append(-1)
        return result
```

