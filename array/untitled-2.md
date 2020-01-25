# 66. Plus One \(easy\)

## Question:

Given a **non-empty** array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

**Example 1:**

```text
Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

## Thought:

* math
* index &gt; 0 or index &lt; 0 \(insert 1 before the index\)

## Solution:

```text
class Solution:
    def plusOne(self, nums: List[int]) -> List[int]:
        if not nums:
            return nums
        i = len(nums) - 1
        while nums[i] == 9:
            nums[i] = 0
            i -= 1
        if i < 0:
            nums.insert(0, 1)
        else:
            nums[i] += 1
        return nums
```

