# 38：字符串的排列 （567）

## Question:

输入一个字符串，打印出该字符串中字符的所有排列。例如输入字符串abc，则打印出由字符a、b、c所能排列出来的所有字符串abc、acb、bac、bca、cab和cba。

## Thought:

* 核心思想是回溯法[https://github.com/fengberlin/Point2offer/blob/master/src/solution/StringPermutation.java](https://github.com/fengberlin/Point2offer/blob/master/src/solution/StringPermutation.java)

## Solution:

```text
class Solution(object):
    def stringPermutation(self, s):
        if not s or len(s) == 0:
            return
        result = []
        self.permutaion(s, result, 0)
        return sorted(set(result)) # remove duplicates
    
    def permutation(self, ss, result, i):
        if i == len(ss) - 1:
            if ss not in result:
                result.append(ss)
        for j in range(i, len(ss)):
            ss[i], ss[j] = ss[j], ss[i]
            self.permutation(ss, result, i+1)
            ss[i], ss[j] = ss[j], ss[i] # return to the original string (backtracking)
```

