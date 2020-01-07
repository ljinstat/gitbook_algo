# 14：剪绳子 \(重要\) \(343\)

## Question:

给你一根长度为n绳子，请把绳子剪成m段（m、n都是整数，n&gt;1并且m&gt;1）。每段的绳子的长度记为k\[0\]、k\[1\]、……、k\[m\]。k\[0\]_k\[1\]_…\*k\[m\]可能的最大乘积是多少？例如当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到最大的乘积18。

## Thought:

* dynamic programming
* f\(i\) 长度为i的绳子剪断后乘积的最大值
* 子问题的最优解储存在数组里，自下而上，避免重复计算
* f\(i\) = f\(j\) \* f\(i-j\)
* **O\(n^2\), O\(n\)**
* Greedy
* 尽可能剪掉长度为3的绳子
* 当 n &gt;= 5 时，
  * 2\(n-2\) &gt; n
  * 3\(n-3\) &gt; n
  * 3\(n-3\) &gt;= 2\(n-2\)
* 长度为4的时候 2\*2 = 4
* **O\(1\), O\(1\)**

## Solution:

```text
class Solution(object):
    def maxProduct(self, length):
        if length < 2:
            return 0
        if length == 2:
            return 2
        if length == 3:
            return 2
        product = [0] * (length + 1)
        product[0], product[1], product[2], product[3] = 0, 1, 2, 3 # ??
        for i in range(4, length+1):
            max_prod = 0
            for j in range(1, i//2+1):
                prod = product[j] * product[i-j] # product[i] max product at index i
                if max_prod < prod:
                    max_prod = prod
                product[i] = max_prod
        max_prod = product[length]
        return max_prod
        # --------------------------
        # greedy
        if n < 2:
            return 0
        if n == 2:
            return 1
        if n == 3:
            return 2
        times_3 = n // 3
        if n - times_3*3 == 1: # length is 4
            times_3 -= 1
            return pow(3, times_3) * 2 * 2
        elif n - times_3*3 == 0:
            return pow(3, times_3)
        else:
            return pow(3, times_3) * 2
        
```

