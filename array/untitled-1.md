# 26. Remove Duplicates from Sorted Array \(easy\)

## Question:

Given a sorted array _nums_, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only _once_ and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O\(1\) extra memory.

**Example 1:**

```text
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

## Thoughts:

Two pointers: fast and slow

if nums\[fast\] == nums\[slow\], skip duplicates

if nums\[fast\] != nums\[slow\], copy the value to nums\[slow+1\]

## Solution:

```text
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        slow = 0
        for fast in range(len(nums)):
            if nums[slow] != nums[fast]:
                slow += 1
                nums[slow] = nums[fast]
        return slow + 1
        # -----------------------------------
        i = 0
        for fast in range(len(nums)):
            if nums[i] != nums[fast]:
                slow += 1
                nums[i] = nums[fast]
        return slow + 1
```



