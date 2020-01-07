# 15：二进制中1的个数 （191）

## Question:

题目描述：请实现一个函数，输入一个整数，输出该数二进制表示中1的个数。例如把9表示成二进制是1001，有2位是1。因此如果输入9，该函数输出2。

## Thought:

* 位运算
* 左移 O\(n\)
* 能给面试官带来惊喜的解法：bit manipulation O\(k\) k: number of 1
* [https://leetcode.com/problems/number-of-1-bits/solution/](https://leetcode.com/problems/number-of-1-bits/solution/)

## Solution:

```text
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n: int
        :rtype: int
        """
        # loop and flip move to the left
        num_1 = 0
        mask = 1
        for i in range(32):
            if n & mask != 0:
                num_1 += 1
            mask <<= 1
        return num_1
        # bit manipulation
        s = 0
        while n != 0:
            n &= (n - 1)
            s += 1
        return s
```

