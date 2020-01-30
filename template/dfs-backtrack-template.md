# DFS backtrack template

examples:

79. word search

## template:

```text
class Solution:
    def main(self, nums):
        if not nums:
            return
        self.dfs(...)
        return results
    def dfs(self, nums,...):
        # exit conditions
        ...
        new_nums = ...
        self.dfs(new_nums, ...)
        nums = ... # backtrack
    
```

## examples:

79. word search \(matrix\)

```text
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        if not board:
            return False
        for i in range(len(board)):
            for j in range(len(board[0])):
                if self.dfs(board, i, j, word):
                    return True
        return False

    def dfs(self, board, i, j, word):
        if len(word) == 0:
            return True
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or board[i][j] != word[0]:
            return False
        temp = board[i][j]
        board[i][j] = '#'
        result = self.dfs(board, i+1, j, word[1:]) or \
                 self.dfs(board, i-1, j, word[1:]) or \
                 self.dfs(board, i, j+1, word[1:]) or \
                 self.dfs(board, i, j-1, word[1:])
        board[i][j] = temp
        return result


```

