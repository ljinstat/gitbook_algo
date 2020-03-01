# Dynamic Programming template

1.  计数

* 有多少种方式走到右下角
* 有多少种方式选出k个数使得和是sum

2. 求最大最小值

* 从左上角到右下角的最大数字和
* 最长上升子序列长度

3. 求存在性

* 取石子游戏，先手是否必胜
* 能不能选出k个数使得和是sum

1. memorization

统计方案个数

```text
# unique paths (DP) 2D to 1D
def unique_paths(m, n):
	if not m or not n:
		return 0
	dp = [[1 for _ in range(n)] for _ in range(m)]
	for i in range(1, m):
		for j in range(1, n):
			dp[i][j] = dp[i-1][j] + dp[i][j-1]
	return dp[-1][-1]
	# -----O(n)--------------
	dp = [1] * n
	for _ in range(1, m):
		for j in range(1, n):
			dp[j] += dp[j-1] 
	return dp[-1]
```



