# 51：数组中的逆序对 \(493 hard 315 hard\)

## Question:

在数组中的两个数字如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数.

## Thought:

* 逆序对的总数=左边数组中的逆序对的数量+右边数组中逆序对的数量+左右结合成新的顺序数组时中出现的逆序对的数量；
* divide and conquer \(graph\)
* [https://www.cnblogs.com/coffy/p/5896541.html](https://www.cnblogs.com/coffy/p/5896541.html)
* Modified merge sort

## Solution:

```text
class Solution(object):
    def inversePairs(self, nums):
        if not nums:
            return 0
        lst = [0] * len(nums)
        count = self.merge(nums, lst, 0, len(nums)-1)
        return count
        
    def merge(self, nums, lst, low, high):
        # only one element left
        if low == high:
            lst[low] = nums[low]
            return 0
        mid = left + (right - left) // 2
        left_count = self.merge(nums, lst, low, mid)
        right_count = self.merge(nums, lst, mid+1, high)
        count = 0
        i = mid # 初始化时i、j指针分别指向第一个和第二个子数组的末尾
        j = high
        idx_lst = high # idx_lst指针指向lst数组的末尾
        while j > mid and i >= low:
            if nums[i] > nums[j]:
                count += j - mid
                lst[idx_lst] = nums[i]
                idx_lst -= 1
                i -= 1
            else:
                lst[idx_lst] = nums[j]
                idx_lst -= 1
                j -= 1
        while i >= low:
            lst[idx_lst] = nums[i]
            idx_lst -= 1
            i -= 1
        while j > mid:
            lst[idx_lst] = nums[j]
            idx_lst -= 1
            j -= 1
        return left_count + right_count + count
```

