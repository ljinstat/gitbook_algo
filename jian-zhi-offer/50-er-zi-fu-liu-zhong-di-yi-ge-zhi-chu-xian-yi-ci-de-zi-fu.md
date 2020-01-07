# 50（二）：字符流中第一个只出现一次的字符

## Question:

请实现一个函数用来找出字符流中第一个只出现一次的字符。例如，当从字符流中只读出前两个字符"go"时，第一个只出现一次的字符是'g'。当从该字符流中读出前六个字符"google"时，第一个只出现一次的字符是'l'。

## Thought:

* Hash Map
* stream是一个list， 还需要一个hash table。每次insert新的character在stream里，都用hash map记录下来。最后check stream里面的每一个字符，在hash map里面的计数是不是1。

## Solution:

```text
class Solution(object):
    def __init__(self):
        self.letter = {}
        self.stream = []
    
    def FirstAppearingOnce(self):
        if self.letter:
            for ch in self.stream:
                if self.letter[ch] == 1:
                    return ch
        else:
            return '#'
        return '#'
        
    def Insert(self, char):
        self.stream.append(char)
        if char in self.letter:
            self.letter[char] += 1
        else:
            self.letter[char] == 1            
```



