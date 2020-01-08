# Bubble sort

第一个元素如果比第二个元素大，两个元素交换，依次类推，交换相邻两个元素，第一次结束交换时最后一个元素是最大的，再重新开始交换直到排序完成

* O\(n^2\), O\(1\)
* stable sorting
* in-place

```text
class Solution():
    def bubble_sort(self, arr):
        if not arr or len(arr) == 1:
            return arr
        n = len(arr)
        for i in range(n): # only to control the last element
            for j in range(n-i-1):
                if arr[j] > arr[j+1]:
                    arr[j], arr[j] = arr[j], arr[i]
        return arr
            
```

优化：如果在一次循环里面都没有发生元素交换，那么说明数组已经是有序的，直接可以结束循环

```text
class Solution():
    def bubble_sort(self, arr):
        if not arr or len(arr) == 1:
            return arr
        n = len(arr)
        for i in range(n): # only to control the last element
            flag = True
            for j in range(n-i-1):
                if arr[j] > arr[j+1]:
                    flag = False
                    arr[j], arr[j] = arr[j], arr[i]
            if flag:
                break
        return arr
```

