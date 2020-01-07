# 88. Merge Sorted Array \(easy\)

## Question:

Given two sorted integer arrays _nums1_ and _nums2_, merge _nums2_ into _nums1_ as one sorted array.

**Note:**

* The number of elements initialized in _nums1_ and _nums2_are _m_ and _n_ respectively.
* You may assume that _nums1_ has enough space \(size that is greater or equal to _m_ + _n_\) to hold additional elements from _nums2_.

**Example:**

```text
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

## Thought:

* copy numbers from the end of the array

## Solution:

```text
Class Solution(object):
    def mergeArray(num1, m, num2, n):
        while m > 0 and n > 0:
            if num1[m-1] >= num2[n-1]:
                num1[m+n-1] = num1[m-1]
                m -= 1
            else:
                num1[m+n-1] = num2[n-1]
                n -= 1
        if n > 0:
            num1[:n] = num2[:n]
             
```

