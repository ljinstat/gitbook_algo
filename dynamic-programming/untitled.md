# 120. Triangle \(medium\)\(triangle matrix\)

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

```text
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is `11` \(i.e., **2** + **3** + **5** + **1**= 11\).

**Note:**

Bonus point if you are able to do this using only _O_\(_n_\) extra space, where _n_ is the total number of rows in the triangle.

## Thought:

* bottom-up and top down
* bottom-up: take the last row as result and modify it in place. the minimal value at this point is the sum of minimal result of the bottom left and right, and the value at this point
* top-down: the same idea, but the edges should be considered.

## Solution:

```text
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        # bottom-up
        if not triangle:
            return -1
        result = list(triangle[-1])
        for i in range(len(triangle) - 2, -1, -1):
            for j in range(len(triangle[i])):
                result[j] = min(result[j], result[j+1]) + triangle[i][j]
        return result[0]  # attention to the return value
        
        # top-down
        if not triangle:
            return 
        results = [[0 for _ in range(len(row))] for row in triangle] # 
        results[0][0] = triangle[0][0]
        for i in range(1, len(triangle)):
            for j in range(len(triangle[i])):
                if j == 0:
                    results[i][j] = results[i-1][j] + triangle[i][j]
                elif j == len(triangle[i]) - 1:
                    results[i][j] = results[i-1][j-1] + triangle[i][j]
                else:
                    results[i][j] = min(results[i-1][j], results[i-1][j-1]) + triangle[i][j]
        return min(results[-1])
```



