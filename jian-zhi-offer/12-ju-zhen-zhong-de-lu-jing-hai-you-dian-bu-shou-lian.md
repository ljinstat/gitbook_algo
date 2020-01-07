# 12：矩阵中的路径 （还有点不熟练）\(79\)

## Question:

请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中任意一格开始，每一步可以在矩阵中向左、右、上、下移动一格。如果一条路径经过了矩阵的某一格，那么该路径不能再次进入该格子。例如在下面的3×4的矩阵中包含一条字符串“bfce”的路径（路径中的字母用下划线标出）。但矩阵中不包含字符串“abfb”的路径，因为字符串的第一个字符b占据了矩阵中的第一行第二个格子之后，路径不能再次进入这个格子。

## Thought:

* backtracking 回溯法 DFS
* 多步骤解决的问题，每个步骤都可以有多个选项。可以用树状结构表示。如果上一个节点的所有可能都已经试过，并且不能达到约束条件的要求，就再次回溯到上一个节点。
* [https://www.youtube.com/watch?v=vYYNp0Jrdv0](https://www.youtube.com/watch?v=vYYNp0Jrdv0)
* 因为每个cell只能路过一次，所以在递归之前要把这个cell清空，在递归之后再改回原来的值。
* **Complexity: time O\(mn**_**4^k\) where k is the length of the string; mn for for loop and for the dfs method its 4^k.Since the dfs method goes only as deep as the word length we have T\(k\)=4\(T\(k-1\)\)=4**_**4T\(k-2\)=....=.. which will be 4^k.** 
* **space O\(4mn\) if the function call stack is taken into account. In each cell, we recursively call its 4four neighbors and there are mn cells in total.** [**http://rainykat.blogspot.com/2017/01/leetcodef-79-word-search-backtracking.html**](http://rainykat.blogspot.com/2017/01/leetcodef-79-word-search-backtracking.html)\*\*\*\*

```text
class Solution(object):
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        # DFS
        if not board:
            return False
        for i in range(len(board)):
            for j in range(len(board[0])):
                if self.dfs(board, i, j, word):
                    return True
        return False
    
    def dfs(self, board, i, j, word):
        if len(word) == 0: # found all letters
            return True
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or board[i][j] != word[0]: # why not i == len(board) ????
            return False 
        temp = board[i][j] # store the previous value
        board[i][j] = '#' # avoid visit again
        result = self.dfs(board, i+1, j, word[1:]) or \
                 self.dfs(board, i-1, j, word[1:]) or \
                 self.dfs(board, i, j+1, word[1:]) or \
                 self.dfs(board, i, j-1, word[1:])
        board[i][j] = temp
        return result
```

