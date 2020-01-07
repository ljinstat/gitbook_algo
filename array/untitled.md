# 243. Shortest Word Distance \(easy\)

## Question:

Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.

For example,  
Assume that words = `["practice", "makes", "perfect", "coding", "makes"]`.

Given word1 = `“coding”`, word2 = `“practice”`, return 3.  
Given word1 = `"makes"`, word2 = `"coding"`, return 1.

Note:  
You may assume that word1 does not equal to word2, and word1 and word2 are both in the list.

## Thought:

[https://github.com/BruceWeng/Leetcode-Python/blob/master/243.%20Shortest%20Word%20Distance.py](https://github.com/BruceWeng/Leetcode-Python/blob/master/243.%20Shortest%20Word%20Distance.py)

## Solution:

```text
class Solution:
    def shortestDistance(self, word, word1, word2):
        if not word or not word1 or not word2:
        idx1 = -1
        idx2 = -1
        result = sys.maxsize
        for i in range(len(word)):
            if word[i] == word1:
                idx1 = i
            elif word[i] == word2:
                idx2 = i
            if idx1 != -1 and idx2 != -1:
                result = min(result, abs(idx2-idx1))
        return result
```

