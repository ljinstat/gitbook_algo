# Quicksort

* Shuffle is needed for performance guarantee.
* Quicksort is an in-place algorithm.
* Quicksort is not stable.
* 整体排序再局部排序

Python:   

```text
class Solution:   
    def sortIntegers(self, arr):
        if not arr or len(arr) == 0:
            return
        self.quickSort(arr, 0, len(arr) - 1)
        
    def partitioner(self, arr, first, last):
        pivot = arr[first] # a value not index or pivot = arr[(first + last // 2)]
        left = first
        right = last
        # must be <= here
        while left <= right:
            while left <= right and arr[left] <= pivot:
                left += 1
            while left <= right and arr[right] >= pivot:
                right -= 1
            if left <= right:
                arr[left], arr[right] = arr[right], arr[left]
                left += 1
                right -= 1
        arr[first], arr[right] = arr[right], arr[first]
        return right # return index
        
    def quickSort(self, arr, first, last):
        if first < last:
            pivot = self.partitioner(arr, first, last)
            self.quickSort(arr, first, pivot-1)
            self.quickSort(arr, pivot+1, last)
```



