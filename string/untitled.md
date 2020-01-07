# 3. Longest Substring Without Repeating Characters （medium）

## Question:

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```text
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

## Thought:

* brute force
* sliding window: at most 2n steps
* optimized sliding window: only n steps
* A sliding window is an abstract concept commonly used in array/string problems. A window is a range of elements in the array/string which usually defined by the start and end indices, i.e. \[ i , j \) \[i,j\) \(left-closed, right-open\). A sliding window is a window "slides" its two boundaries to the certain direction. For example, if we slide \[ i , j \) \[i,j\) to the right by 1 1 element, then it becomes \[ i + 1 , j + 1 \) \[i+1,j+1\) \(left-closed, right-open\).

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

