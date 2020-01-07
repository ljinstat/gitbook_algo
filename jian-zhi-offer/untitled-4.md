# 39：数组中出现次数超过一半的数字 \(169\)

## Question:

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1, 2, 3, 2, 2, 2, 5, 4, 2}。由于数字2在数组中现了5次，超过数组长度的一半，因此输出2。

## Thought:

* hash map
* sorting \(quick sort\)
* **Boyer-Moore Voting Algorithm: 记录当前的count， 如果遇到的不是current的数，count减1. 对于一个出现了多于半数的数字，它的count一定比其他数字大，所以count一定是正的。**
* 如果函数输入的是一个指针，要考虑是不是为空。
* assumption: null/ empty: None.
* complexity: O\(n\), O\(1\)

## Solution:

```text
class Solution(object):
    def majorityElement(self, nums):
        # hashmap
        count = collections.Counter(nums)
        return max(count.keys(), key=count.get) # travers all element in keys and get the key with maximum
        # Boyer-Moore Voting 
        if not nums or len(nums) == 0:
            return None
        count = 0
        current = 0
        for num in nums:
            if count == 0:
                current = num
            elif current == num:
                count += 1
            else:
                count -= 1
        return current
```

