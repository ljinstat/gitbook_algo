# two pointers template

1. one direction two pointers

slow and fast pointers:

* remove elements
* remove duplicates from sorted array I / II
* move zeros 为什么是 ！=0？把i想成fast index，last\_nonzero是slow，相当于是把右边非零的数置换到左边。

```text
def move_zeros(nums):
	if not nums:
		return nums
	last_nonzero = 0
	for i in range(len(nums)):
		if nums[i] != 0:
			nums[i], nums[last_nonzero] = nums[last_numzero], nums[i]
			last_nonzero += 1
	return nums
```



