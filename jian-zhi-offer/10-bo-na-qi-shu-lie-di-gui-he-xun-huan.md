# 10：斐波那契数列 （递归和循环）

## Question:

n = 0时，f\(n\) = 0；n = 1时，f\(n\) = 1；n &gt; 1时，f\(n\) = f\(n - 1\) + f\(n - 2\)

## Thought:

* 递归: 简洁；**每一次函数调用都要在内存栈中分配空间保存参数、返回地址和临时变量，效率不如循环。调用栈溢出**。
* 青蛙跳台阶问题
* 小矩形覆盖大矩形

## Solution:

```text
class Solution(object):
    def fib(self, N):
        """
        :type N: int
        :rtype: int
        """
        if N < 0:
            return 0
        if N == 1:
            return 1
        return self.fib(N-1) + self.fib(N-2)
        # --------------------------
        # memotization
        if N < 0:
            return 0
        if N == 1:
            return 1
        fibone = 1
        fibtwo = 0
        fibn = 0
        for _ in range(2, N+1):
            fibn = fibone + fibtwo
            fibtwo = fibone
            fibone = fibn
        return fibn
```

