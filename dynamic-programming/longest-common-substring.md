# Longest common substring

```text
def longest_substring(self, a, b):
	if not a or not b:
		return 0
	m = len(a)
	n = len(b)
	max_len = 0
	dp = [[0]*(n+1) for _ in range(m+1)]
	for i in range(m):
		for j in range(n):
			if a[i] == b[j]:
				dp[i+1][j+1] = dp[i][j] + 1
				max_len = max(max_len, dp[i+1][j+1])
			else:
				dp[i+1][j+1] = 0
	return max_len
```

