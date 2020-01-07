# 21：调整数组顺序使奇数位于偶数前面

## Question:

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。

## Thought:

* **双指针**：第一个指针在数组开头，另一个指最后一个数字。第一个指针在指向奇数的时候，挪到下一位。第二个指针指向奇数的时候不动，指向偶数的时候，向前一位。当第一个指针指向偶数，第二个指向奇数的时候，两个数互换。
* 如果改成数组中的数按照大小分为两个部分，负数在非负数的前面。或者能被3整除的数都在前面，反之在后面。只要改变判断条件的函数就可以了。**所以更优的方案是添加一个函数，判断是否是奇偶，这样提高了代码的扩展性和重用性。**
* **assumption: in-place?** 

## Solution：

```text
class Solution(object):
    def numberString(self, num):
        # two pointers
        if not num:
            return
        left = 0
        right = len(num) - 1
        while left < right:
            while left < right and not self.isEven(num[left]):
                left += 1
            while left < right and self.isEven(num[right]):
                right -= 1
            num[left], num[right] = num[right], num[left]
            
    def isEven(self, n):
        return True if n & 1 == 0 else False 
    
```

