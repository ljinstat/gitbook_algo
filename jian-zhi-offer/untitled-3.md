# 13：机器人的运动范围

## Question:

地上有一个m行n列的方格。一个机器人从坐标\(0, 0\)的格子开始移动，它每一次可以向左、右、上、下移动一格，但不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格\(35, 37\)，因为3+5+3+7=18。但它不能进入方格\(35, 38\)，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

## Thought:

## Solution:

```text
class Solution(object):
    def movingCount(self, threshold, rows, cols):
        if threshold < 0 or rows <= 0 or cols <= 0:
            return False
        visited = [[0 for j in range(cols)] for i in rows]
        count = self.movingMain(self, threshold, rows, cols, 0, 0, visited)
        return count
        
    def movingMain(self, threshold, rows, cols, i, j, visited):
        count = 0
        visited[i][j] = True
        if self.check(threshold, rows, cols, i, j, visited):
            count = 1 + self.movingMain(threshold, rows, cols, i+1, j, visited) \
                    + self.movingMain(threshold, rows, cols, i-1, j, visited) \
                    + self.movingMain(threshold, rows, cols, i, j+1, visited) \
                    + self.movingMain(threshold, rows, cols, i, j-1, visited)
        return count
    
    def check(self, threshold, rows, cols, i, j, visited):
        if i > 0 and i < rows and j > 0 and j < cols and visited[i][j]:
            return True
        sum_row_col = i // 10 + i % 10 + j // 10 + j % 10
        if sum_row_col <= threshold:
            return True
        return False 
```

