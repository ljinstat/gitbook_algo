# 17：打印1到最大的n位数 \(还是有点搞不清楚\)

## Question:

输入数字n，按顺序打印出从1最大的n位十进制数。比如输入3，则打印出1、2、3一直到最大的3位数即999。

## Thought:

* 简单解法，**大数问题，字符串来解决大数**问题
* 解法一：在字符串的数字上模拟加法，字符串表达的数字打印出来
* 解法二：全排列，递归， 把数字的每一位都从0到9排列一遍
* 前面的代码中，我们都是用一个char型字符表示十进制数字的一位。8个bit的char型字符最多能表示256个字符，而十进制数字只有0-9的10个数字。因此用char型字符串来表示十进制的数字并没有充分利用内存，有一些浪费。有没有更高效的方式来表示大数。 （bitmap）
* [https://blog.csdn.net/u013063153/article/details/70800381](https://blog.csdn.net/u013063153/article/details/70800381)
* assumption: input: n; output: print numbers; null/empty: " "

## Solution:

```text
class Solution(object):
    def print1toMaxDigits(self, n):
        num = ['0'] * n
        while not increment(num):
            printNumber(num)
        return
    
    def increment(self, num):
        # add 1 to num, check if it overflows
        isOverflow = False
        nTakeOver = 0
        nLength = len(num)
        for i in range(nLength-1, -1, -1):
            nSum = ord(num[i]) - ord('0') + nTakeOver
            if i == nLength - 1:
                nSum += 1
            if nSum >= 10:
                if i == 0: # the first digit
                    isOverflow = True # whether increte one digit
                else:
                    nSum -= 10
                    nTakeOver = 1
                    num[i] = str(nSum)
            else:
                num[i] = str(nSum)
        return isOverflow
    
    def printNumber(self, num):
        isBeginning0 = True
        nLength = len(num)
        for i in range(nLength):
            if isBeginning0 and num[i] != 0:
                isBeginning0 = False
            if not isBeginning0:
                print('%c'%number[i]) # character
        print(' ')
    # ----------------------------------------------
    def printRecursion(self, num, length, idx):
        if idx == length - 1:
            printNumber(num)
            return
        for i in range(10): # 0-9
            num[idx + 1] = str(i)
            printRecursion(num, length, idx+1)
```

