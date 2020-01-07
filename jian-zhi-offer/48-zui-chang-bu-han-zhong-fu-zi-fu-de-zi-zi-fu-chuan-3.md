# 48：最长不含重复字符的子字符串 \(3\)

## Question:

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。假设字符串中只包含从'a'到'z'的字符。例如：在字符串"arabcacfr"中，最长的不包含重复字符的子字符串是"acfr"，长度为4。

## Thought:

* sliding window 看3
* **dynamic programming \(未完成\)**

## Solution:

```text
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        # using HashSet as a sliding window, checking if a character in the current can be done in O(1)
        # solution requires at most 2n steps
        n = len(s)
        letter = set()
        result = 0
        left, right = 0, 0 # two boundaries
        while left < n and right < n:
            if s[right] not in letter:
                letter.add(s[right])
                right += 1
                result = max(result, right - left)
            else:
                letter.remove(s[left])
                left += 1
        return result
        # sliding window optimized
        n = len(s)
        result = 0
        letter = {}
        left = 0
        for right in range(n):
            if s[right] in letter:
                left = max(letter[s[right]], left) # skip the duplicated letter
            result = max(result, right - left + 1)
            letter[s[right]] = right + 1
        return result 
```

