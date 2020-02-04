# 44：数字序列中某一位的数字 \(400\) \(巨恶心\)

## Question:

数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从0开始计数）是5，第13位是1，第19位是4，等等。请写一个函数求任意位对应的数字

## Thought:

* 
* **O \(logn\)**

## Solution:

```text
class Solution(object):
    def findNthDigit(self, n):
        """
        :type n: int
        :rtype: int
        """
        digit = 1
        start = 1
        step = 9
        digit_sum = 0
        while n > step * start * digit:
            digit_sum += step * start * digit
            start *= 10
            digit += 1
        # n - digit_sum = x*digit + 1, looking for x
        residu = n - digit_sum - 1 # ??? I cannot understand from that
        result = residu // digit + start # find the number 
        return str(result)[residu % digit]
```

