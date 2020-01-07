# 200. Number of Islands \(medium\) BFS

## Quesiton:

Given a 2d grid map of `'1'`s \(land\) and `'0'`s \(water\), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```text
Input:
11110
11010
11000
00000

Output: 1
```

## Thought:

* BFS: only select point with '1', traverse surronding '1', and replace the value with '0'
* representation of the coordinate with x+delta, y+delta

## Solution:

```text
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid or len(grid) == 0:
            return 0
        result = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    self.bfs(grid, i, j)
                    result += 1
        return result
                    
    def bfs(self, grid, x, y):
        dq = collections.deque([(x, y)])
        grid[x][y] = '0'
        while dq:
            x, y = dq.popleft() # error forget to pop a value
            for delta_x, delta_y in [(-1, 0), (1, 0), (0, -1), (0, 1)]:
                new_x = x + delta_x
                new_y = y + delta_y
                if not self.isValid(grid, new_x, new_y):
                    continue
                dq.append((new_x, new_y))
                grid[new_x][new_y] = '0' # if it is equal to 1, replace it with 0
        
    def isValid(self, grid, x, y):
        return 0 <= x < len(grid) and 0 <= y < len(grid[0]) and grid[x][y] == '1'
        
```

