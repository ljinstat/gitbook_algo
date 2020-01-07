# 16：数值的整数次方 \(50\)

## Question:

实现函数double Power\(double base, int exponent\)，求base的exponent次方

## Thought:

* 三种错误的处理方式：返回值、全局变量、异常
* 当base = 0， exponent = 0 或者同时等于0
* 高效的方法：位与运算判断奇偶数，如果与1取与，等于1的是奇数，因为偶数只有一个1
* 递归

## Solution:

```text
class Solution(object):
    
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n == 0:
            return 1
        if n == 1:
            return x
        
        get_invalid = False
        if n < 0 and x == 0:
            get_invalid = True # base is zero and exponent is negative
            return 0
        if n < 0:
            return 1 / self.myPow(x, -n)
        
        half = self.myPow(x, n // 2)
        if n & 1 == 1: # odd
            return half * half * x
        else:
            return half * half
```

