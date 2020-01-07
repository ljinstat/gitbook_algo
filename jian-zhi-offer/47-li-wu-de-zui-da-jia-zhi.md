# 47：礼物的最大价值

## Question:

在一个m×n的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值价值大于0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向**右**或者向下移动一格直到到达棋盘的右下角。给定一个棋盘及其上面的礼物，请计算你最多能拿到多少价值的礼物？

## Thought:

*  某一个点 \[i, j\] 要通过 \[i-1, j\] 和 \[i, j-1\] 达到
* 如果用 2D 矩阵， 每个元素都会被保存
* 如果用 1D 数组，只有 \[i, 0--j-1\] 和 \[i-1, j--col-1\] 需要被保存 ??????
* 时间和空间的效率理解，可以不用二维的数组
* 动态规划

## Solution:

```text
class Solution(object):
    def maxValueofGift(self, values):
        # using 2D matrix
        if not values:
            return 0
        row = len(values)
        col = len(values[0])
        if row == 0 or col == 0:
            return 0
        max_value = [[0 for _ in range(col)] for _ in range(row)]
        for i in range(row):
            for j in range(col):
                if col > 0:
                    left = max_value[i][j - 1] # previous step is the left
                if row > 0:
                    up = max_value[i - 1][j] # previous step is the up 
                max_value[i][j] = max(left, up) + values[i][j]
        return max_value[row - 1][col - 1]
        # using 1D array
        if not values:
            return 0
        row = len(values)
        col = len(values[0])
        if row == 0 or col == 0:
            return 0
        max_value = [0 for _ in range(row)]
        for i in range(row):
            for j in range(col):
                if col > 0:
                    left = max_value[j - 1]
                if row > 0:
                    up = max_value[j] # Should it be down?
                max_value[j] = max(left, up) + values[i][j]
        return max_value[col - 1]           
```

