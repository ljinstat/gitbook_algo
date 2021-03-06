# 29：顺时针打印矩阵（54）

## Question:

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

## Thought:

[https://leetcode.com/problems/spiral-matrix/discuss/20599/Super-Simple-and-Easy-to-Understand-Solution](https://leetcode.com/problems/spiral-matrix/discuss/20599/Super-Simple-and-Easy-to-Understand-Solution)

## Solution:

```text
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        # simulation
        if not matrix:
            return []
        R, C = len(matrix), len(matrix[0])
        visited = [[False] * C for _ in matrix]
        result = []
        dr = [0, 1, 0, -1]
        dc = [1, 0, -1, 0]
        r = c = di = 0
        for _ in range(R * C):
            result.append(matrix[r][c])
            visited[r][c] = True
            cr, cc = r + dr[di], c + dc[di] # next index
            if 0 <= cr < R and 0 <= cc < C and not visited[cr][cc]:
                r, c = cr, cc # next row and col
            else:
                di = (di + 1) % 4 # if it touches the bound, turn to the next direction
                r, c = r + dr[di], c + dc[di]
        return result
        # layer by layer
        if not matrix:
            return []
        result = []
        r = len(matrix)
        c = len(matrix[0])
        left, right = 0, c - 1
        up, down = 0, r - 1
        while len(result) < r * c:
            for i in range(left, right+1): 
                if len(result) < r * c:# left to right
                    result.append(matrix[up][i])
            for j in range(up+1, down): 
                if len(result) < r * c: # up to down
                    result.append(matrix[j][right])
            for k in range(right, left-1, -1):
                if len(result) < r * c:
                    result.append(matrix[down][k])
            for h in range(down-1, up, -1):
                if len(result) < r * c:
                    result.append(matrix[h][left])
            left += 1
            right -= 1
            up += 1
            down -= 1
        return result
                
```

