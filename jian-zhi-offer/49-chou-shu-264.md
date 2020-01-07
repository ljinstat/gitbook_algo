# 49：丑数 \(264\)

## Question:

我们把只包含质数因子2、3和5的数称作丑数（Ugly Number）。求按从小到大的顺序的第1500个丑数。例如6、8都是丑数，但14不是，因为它包含因子7。习惯上我们把1当做第一个丑数。

## Thought:

* t2、t3、t5分别指向比较大小后的还未乘以2，3，5的最小丑数的下标
* 例如现在丑数序列为{1, 2}，在1_2，1_3，1_5比较后并且选出1_2为最小之后，t2需要向前移动，然后再比较下一个丑数\(此时t2指向的下标的数乘以2\)和他们之间的大小
* [https://leetcode.com/problems/ugly-number-ii/discuss/69362/O\(n\)-Java-solution](https://leetcode.com/problems/ugly-number-ii/discuss/69362/O%28n%29-Java-solution)
* 每一次比较三个序列的当前值，最小的那个值的index要加上1；最终结果是序列的最后一个值。
* assumption: input: int, output: int; null/ empty: 0; all positive?

## Solution:

```text
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        if not n or n <= 0:
            return 0
        result = [1] * n
        result[0] = 1
        # regard it as three sequences, x * 2, y * 3, z * 5
        # then merge three sequences
        i2, i3, i5 = 0, 0, 0
        for i in range(1, n):
            result[i] = min(result[i2]*2, result[i3]*3, result[i5]*5)
            if result[i] == result[i2]*2:
                i2 += 1
            if result[i] == result[i3]*3:
                i3 += 1
            if result[i] == result[i5]*5:
                i5 += 1
        return result[-1]
```

