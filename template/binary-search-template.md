# binary search template

binary search:

 1. without a single given target increasing/ decreasing/ peak/ vally sequence 

* find peak element 
* find minimum in rotated sorted array 
* maximum number in mountain sequence

2. with a target \(= &lt; &gt; target\)

* find first and last position of element in sorted array
* first bad version
* search in a sorted array of unknown size
* search in rotated sorted array\(start and mid\)
* sqrt\(x\)

```text
left = 0
right = len(nums) - 1
while left + 1 < right:
    mid = left + (right - left) // 2
    if nums[mid] == target: (nums[mid] > nums[mid+1] and nums[mid] > nums[mid-1])
    ....
if nums[left] == target:
    return left
...
```

