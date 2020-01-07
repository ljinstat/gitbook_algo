# 30：包含min函数的栈 \(155\)

## Question:

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的min函数。在该栈中，调用min、push及pop的时间复杂度都是O\(1\)。

## Thought:

* 可以借助另外一个栈，把当前最小的值push到栈里，这样pop出来的都是最小的值。

## Solution:

```text
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack = []

    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        self.stack.append((x, min(self.getMin(), x)))
        

    def pop(self):
        """
        :rtype: None
        """
        self.stack.pop()
        

    def top(self):
        """
        :rtype: int
        """
        if self.stack:
            return self.stack[-1][0]
        else:
            return None
        

    def getMin(self):
        """
        :rtype: int
        """
        if self.stack:
            return self.stack[-1][1]
        else:
            return sys.maxint
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

