# n sum template

## Explain

1. sort
2. condition
3. compare the sum of left and right with the target

```text
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        if not nums or len(nums) == 0:
            return []
        results = []
        nums = sorted(nums) # 1. sort
        for i in range(len(nums)-2): # if n > 2
            if nums[i] > 0: # 2. conditions
                break
            first = nums[i]
            if i > 0 and nums[i-1] == first:
                continue
            target = - nums[i]
            left = i + 1
            right = len(nums) - 1
            while left < right: # 3. compare
                if nums[left] + nums[right] == target:
                    results.append([first, nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while left < right and nums[left-1] == nums[left]:
                        left += 1
                    while left < right and nums[right+1] == nums[right]:
                        right -= 1
                elif nums[left] + nums[right] < target:
                    left += 1
                else:
                    right -= 1
        return results
                
```

