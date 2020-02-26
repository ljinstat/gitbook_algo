# Partition QuickSelect template

1. find a target number, return its index 

Lintcode 31 Partition Array

```text
def partition_array(nums, k):
	if not nums:
		return -1
	left = 0
	right = len(nums) - 1
	while left < right:
		while left < right and nums[left] > k:
			left += 1
		while left < right and nums[right] <= k:
			right -= 1
		if left < right:
			nums[left], nums[right] = nums[right], nums[left]
			left += 1
			right -= 1
	if nums[right] >= k:
		return right
	else:
		return right + 1  
```

2. QuickSort

*  main function
* partition output pivot index
* sort divide and conquer

find a pivot index

```text
class Solution:
	
	def quick_sort(self, nums):
		if not nums:
			return 
		self.qs(0, len(nums)-1, nums)
		return nums

	def partition(self, nums, first, last): # first and last
		pivot = nums[first] # pivot = random.randint(left, right)
		left = first
		right = last
		while left <= right:
			while left <= right and nums[left] <= pivot:
				left += 1
			while left <= right and nums[right] >= pivot:
				right += 1
			if left <= right:
				nums[left], nums[right] = nums[right], nums[left]
				left += 1
				right -= 1
		nums[right], nums[first] = nums[first], nums[right]
		return right

	def qs(self, first, last, nums):
		if first < last:
			pivot = self.partition(nums, first, last)
			self.qs(first, pivot-1, nums)
			self.qs(pivot+1, last, nums)
```

3. Quick Select

* main function  len\(nums\) - k

```text
def k_largest(self, nums, k):
	if not nums or k > len(nums) - 1 or k < 0:
		return
	return self.partition(nums, 0, len(nums) - 1, len(nums) - k)
	
def partition(self, nums, start, end, k):
        """
    During the process, it's guaranteed start <= k <= end
    """
    # partition是什么？
    # 找到一个pivot使得它左边的值都小于它，右边的值都大于它
    # 在无序的array中，如果target是一个具体的数值，output是pivot index
    # 如果target是一个index，output是partition之后的这个index上的值
    # pivot index 选择在中点就不用调换
    if start == end:
        return nums[k]
        
    left, right = start, end
    pivot = nums[(start + end) // 2]
    while left <= right:
        while left <= right and nums[left] < pivot: # 这里不要加=
            left += 1
        while left <= right and nums[right] > pivot:
            right -= 1
        if left <= right:
            nums[left], nums[right] = nums[right], nums[left]
            left, right = left + 1, right - 1
            
    # left is now bigger than right
    if k <= right:
        return self.partition(nums, start, right, k)
    if k >= left:
        return self.partition(nums, left, end, k)
    
    return nums[k]
```

4. merge sort 

* main function \(mergesort\)
* sort divide and conquer \(mergesort, mergesort, merge\)
* merge \(two sets of pointers: start end, left right\) \(return self.results\)
* 先对半分，再从下到上合成

```text
class Solution:
	def __init__(self):
		self.results = []

	def sort_integer(self, nums):
		if not nums:
			return 
		self.mergesort(nums, 0, len(nums)-1)
		
	def mergesort(self, nums, start, end):
		if start < end:
			mid = start + (end - start) // 2
			self.mergesort(nums, start, mid)
			self.mergesort(nums, mid + 1, end)
			self.merge(nums, start, end)
			
	def merge(self, nums, start, end):
		mid = start + (end - start) // 2
		left = start
		right = mid + 1
		while left <= right and right <= end:
			if nums[left] < nums[right]:
				self.results.append(nums[left])
				left += 1
			else:
				self.results.append(nums[right])
				right += 1
		self.results += nums[left:right]
		self.results += nums[right:end+1]
		return self.results
```

