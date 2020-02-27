# Dynamic Programming template

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



