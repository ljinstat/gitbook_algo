# 9：用两个栈实现队列 \(232\)

## Question:

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数appendTail和deleteHead，分别完成在队列尾部插入结点和在队列头部删除结点的功能。

## Thought:

* 栈 \(stack\) ：操作系统会给每个线程创建一个栈用来存储函数调用时各个函数的参数、返回地址和临时变量等。最后被 push 的元素会被第一个 pop 出去。
* 队列（queue）：先进先出。 
* push O\(1\) and pop amortize O\(1\)

## Solution:

```text
class MyQueue(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.stack1 = []
        self.stack2 = []

    def push(self, x):
        """
        Push element x to the back of queue.
        :type x: int
        :rtype: None
        """
        self.stack1.append(x)
        

    def pop(self):
        """
        Removes the element from in front of queue and returns that element.
        :rtype: int
        """
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop()
        

    def peek(self):
        """
        Get the front element.
        :rtype: int
        """
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2[-1]

    def empty(self):
        """
        Returns whether the queue is empty.
        :rtype: bool
        """
        return True if not self.stack1 and not self.stack2 else False
```

