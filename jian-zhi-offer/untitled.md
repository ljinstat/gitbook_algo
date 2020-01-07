# 6：从尾到头打印链表

## Question:

输入一个链表的头结点，从尾到头反过来打印出每个结点的值。

## Thought:

* 在面试中，如果我们打算修改输入的结构，最好先问面试官是否允许修改。
* **stack 和递归：栈 （stack）与迭代和递归的关系。本质上，栈是一个递归的结构。**
* assumption: change the list? input: head of list; output: print; null/empty: don't exist

## Solution:

```text
class Solution(object):
    def printLinkedlist(head):
        # iteration
        if not head:
            return 'No node exists!'
        stack = []
        while head.next:
            stack.append(head)
            head = head.next
        while stack:
            stack.pop()
        # ----------------
        # recursion
        if not head:
            return 'No node exists!'
        if head.next:
            printLinkedlist(head.next)
        print(head.val)
```

