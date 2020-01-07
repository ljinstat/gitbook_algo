# Summary

## Structure:

while: while start + 1 &lt; end: \# neighbors

**第一部分就只要缩小范围**mid = start + \(end - start\) // 2  
**第二部分再找到结果 条件其实就是跟target比大小，如果等于是怎么样，大于和小于是怎么样**还是在while里面判断和输出等于target的时候比较好，不然会一直呆在循环里面

**第三部分换index  
第四部分：double check**

## **Questions:**

**variations 1: without a single given target**

* find minimum in totated sorted array
* find peak element
* maximum number in mountain sequence
* search in rotated sorted array

variations 2: with a single target, array well sorted

* first bad version
* search in a sorted array of unknown size



