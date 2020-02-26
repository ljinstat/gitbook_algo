# two pointers template

1. one direction two pointers

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

