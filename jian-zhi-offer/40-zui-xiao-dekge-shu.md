# 40：最小的k个数 \(215 kth largest number\) \(最大堆，红黑树，海量数据\) （重要）

## Question:

这8个数字，则最小的4个数字是1、2、3、4。输入n个整数，找出其中最小的k个数。例如输入4、5、1、6、2、7、3、8

## Thought:

* 1. 如果可以修改数组，可以用**partition**改变数字的顺序 O\(n\)
  2. 考虑最坏情况下，每次 partition 将数组分为长度为 N-1 和 1 的两部分，然后在长的一边继续寻找第 K 大，此时时间复杂度为 O\(N^2 \)。不过如果在开始之前将数组进行随机打乱，那么可以尽量避免最坏情况的出现。而在最好情况下，每次将数组均分为长度相同的两半，运行时间 T\(N\) = N + T\(N/2\)，时间复杂度是 O\(N\)。
  3. [https://selfboot.cn/2016/09/01/lost\_partition/](https://selfboot.cn/2016/09/01/lost_partition/)
* 特别适合处理海量数据，O\(nlogk\)
* 先创建一个大小为k的数据容器来储存最小的k个数字。每次从n个数字中取一个，如果容器没有满，直接加上这个数字；如果容器满了，跟容器里的最大值比，如果比最大值小，把这个数替换最大值；如果比最大值大，跳过看下一个数。
* 2. 找到数字中的最大值，容易联想到最大堆，根节点的值总是大于其他任意节点的值。**每次可以在O\(1\)下找到最大值，但是需要O\(logk\)完成删除和插入。**Python 里的heapq是min heap，要用负值把min heap转成max heap。heappop 总是先push一个值，再pop出最小的值。
* 如果是求k个最小的值，直接用min heap就行，不用转变成负值。
* 3. 也可以利用**红黑树**完成。
* 不同的解法：问数据量有多大，能否一次性载入，是否能改变输入的数据
* **在某个数据容器里频繁查找和替换最大值的时候，二叉树是一个合适的选择。**

## Solution:

```text
class Solution(object):
    def smallestKnumbers(self, nums, k):
        # k largest numbers
        if not nums or len(nums) < k:
            return None
        max_heap = []
        for num in nums:
            if len(max_heap) < k:
                heapq.heappush(max_heap, -num) # turn min heap into max heap
            else:
                heapq.heappop(max_heap, -num) # push -num then pop the smallest value
        return list(map(lambda x: -x, max_heap))
        # kth largest number
        # O(k+(n-k)lgk) time, min-heap
        def findKthLargest4(self, nums, k):
            heap = []
            for num in nums:
                heapq.heappush(heap, num)
            for _ in xrange(len(nums)-k): # pop N - k smallest numbers
                heapq.heappop(heap)
            return heapq.heappop(heap)
        # partition-------------------------
        start, end = 0, len(nums) - 1
        while start < end:
            pos = self.partition(nums, start, end)
            if pos == k - 1:
                return nums[:k-1]
            elif pos < k - 1:
                start = pos + 1
            else:
                end = pos - 1
```

## Partition:

```text
def partition1(nums, start, end):
    pivot = nums[start]
    pos = start # the smallest index where numbers to the left are smaller than pivot
    for i in range(1, end):
        if nums[i] <= pivot:
            pos += 1
            if pos != i:
                nums[pos], nums[i] = nums[i], nums[pos]
    nums[start], nums[pos] = nums[pos], nums[start]
    return pos
```

```text
def partition2_3(nums, start, end):
    pivot = nums[start]
    while start < end:
        while start < end and nums[end] >= pivot:
            end -= 1
            # nums[start] = nums[end]
        while start < end and nums[start] <= pivot:
            start += 1
            # nums[end] = nums[start]
        nums[start], nums[end] = nums[end], nums[start]
    nums[start] = pivot
    return start
```

