# 45：把数组排成最小的数 \(179\)

## Question:

输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。

## Thought:

数组中所有的数拼接后有可能会超过整数的范围，因此本题必须要使用字符串来处理。 要对3，32 ，321 排序，不能直接比较32，3的大小，应该比较323，332的大小，即，3，32的大小应该有323，332的大小来确定。因此3比32大，3应该在32后面，32和321比较时，32321&gt;32132,因此32&gt;321,32在321后面，3，32，321由小到大排序为，321，32，3，组成的最小数为：321323

版权声明：本文为CSDN博主「HankingHu」的原创文章，遵循CC 4.0 by-sa版权协议，转载请附上原文出处链接及本声明。 原文链接：[https://blog.csdn.net/u013309870/article/details/66530205](https://blog.csdn.net/u013309870/article/details/66530205)

* assumption: input: array; output: an integer; null/empty: return "0"

## Solution:

```text
import functools # need it in python 3
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        if not nums or len(nums) == 0 or not any(nums):
            return "0"
        compare = lambda x, y: 1 if x + y > y + x else (- 1 if x + y < y + x else 0)
        num_str = map(str, nums) # a list of strings
        return ''.join(sorted(num_str, key=functools.cmp_to_key(compare)))
```



