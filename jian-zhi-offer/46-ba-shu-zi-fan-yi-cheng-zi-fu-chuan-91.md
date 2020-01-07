# 46：把数字翻译成字符串 \(91\)

## Question:

给定一个数字，我们按照如下规则把它翻译为字符串：0翻译成"a"，1翻译成"b"，……，11翻译成"l"，……，25翻译成"z"。一个数字可能有多个翻译。例如12258有5种不同的翻译，它们分别是"bccfi"、"bwfi"、"bczi"、"mcfi"和"mzi"。请编程实现一个函数用来计算一个数字有多少种不同的翻译方法。

## Thought:

* 动态规划
* dp\[0\] 是空值的可能翻译方式； dp\[1\] 是长度为1的string可能的翻译方式。dp\[i\] 是长度为 i 的 string 可能的翻译方式。

## Solution:

```text
class Solution:
    def numDecodings(self, s: str) -> int:
        if not s or len(s) == 0:
            return 0
        dp = [0] * (len(s) + 1)
        # the way of decoding for empty string
        dp[0] = 1
        # the way of decoding for the first number
        dp[1] = 1 if s[0] != '0' else 0
        for i in range(2, len(s)+1):
            first = int(s[i-1:i])
            second = int(s[i-2:i])
            if first >= 1 and first <= 9:
                dp[i] += dp[i-1]
            if second >= 10 and second <= 26:
                dp[i] += dp[i-2]
        return dp[len(s)]
```

