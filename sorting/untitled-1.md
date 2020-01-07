# 179. Largest Number \(medium\)

## Question:

Given a list of non negative integers, arrange them such that they form the largest number.

**Example 1:**

```text
Input: [3,30,34,5,9]
Output: "9534330"
```

## Thought:

It is a descending order. From big to small. \[10, 2\]: 102 &lt; 210 -&gt; 210 -&gt; 2 &gt; 10 -&gt; \[2, 10\]

## Solution:

```text
import functools
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        if not nums or len(nums) == 0 or not any(nums):
            return "0"
        compare = lambda x, y: - 1 if x + y > y + x else (1 if x + y < y + x else 0)
        num_str = map(str, nums) # a list of strings
        return ''.join(sorted(num_str, key=functools.cmp_to_key(compare)))
```

