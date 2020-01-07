# 43：从1到n整数中1出现的次数 \(233\)

## Question:

输入一个整数n，求从1到n这n个整数的十进制表示中1出现的次数。例如输入12，从1到12这些整数中包含1 的数字有1，10，11和12，1一共出现了5次。

## Thought:

* math
* O\(logn\)
* x = abcdefg
* if d == 1: abc \* 1000 + defg + 1
* if d &gt; 1: abc \* 1000 + 1000
* if d == 0: abc \* 1000 

## Solution:

```text
class Solution(object):
    def countDigitOne(self, n):
        """
        :type n: int
        :rtype: int
        """
        # math
        if n <= 0:
            return 0
        # x is number of digits
        num, x, result = n, 1, 0
        while num:
            digit = num % 10
            num /= 10
            result += num * x
            if digit == 1:
                result += n % x + 1
            elif digit > 1:
                result += x
            x *= 10
        return result
```

