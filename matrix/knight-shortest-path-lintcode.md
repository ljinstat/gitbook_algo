# Knight Shortest Path \(lintcode\) BFS

## Question:

Given a knight in a chessboard \(a binary matrix with 0 as empty and 1 as barrier\) with a source position, find the shortest path to a destination position, return the length of the route. Return -1 if knight can not reached.

The knight can go to 8 positions around him. 

## Thought:

* BFS
* input: a matrix, the source and the destination
* 1. edge cases
  2. create a queue, and the initial result 0
  3. level order traversal, each level add one until it can reach the destination, the possible movement can be 8 positions, make sure it does not go out of the bound, turn traversed position to be true \(visited\)

## Solution:

```text
class Solution():
    def knightPath(self, source, destination, grid):
        if not grid or len(grid) == 0 or not source or not destination:
            return -1
        dq = collections.deque(source)
        result = 0
        step_x = [1, 1, -1, -1, 2, 2, -2, -2]
        step_y = [2, -2, 2, -2, 1, -1, 1, -1]
        step = zip(step_x, step_y)
        n = len(grid)
        m = len(grid[0])
        destination = [n-1, m-1]
        while dq:
            size = len(dq)
            for _ in size:
                x, y = popleft()
                if [x, y] == destination:
                    return result
                for delta_x, delta_y in step:
                    new_x = x + delta_x
                    new_y = y + delta_y
                    if self.isValid(new_x, new_y) and not grid[new_x][new_y]:                        
                        dq.append((new_x, new_y))
                        grid[new_x][new_y] = True
            result += 1
        return -1
        
        def isValid(self, grid, x, y):
            return 0 <= x < len(grid) and 0 <= y < len(grid[0]) and grid[x][y] == 1
```

