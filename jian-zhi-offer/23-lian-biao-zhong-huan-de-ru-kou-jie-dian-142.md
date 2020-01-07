# 23：链表中环的入口结点（142）

## Question:

一个链表中包含环，如何找出环的入口结点？

## Thought:

* 这道题可以分为两步：
* 确定链表中有环 （如果快的追上慢的） -≥ 快慢指针相遇的位置离头结点和环的入口的距离相等，同时从头结点和相遇节点出发，再次相遇的节点就是环的入口
* 如果有环的话：a + b + c + b = 2\(a + b\) --&gt; a = c 从头出发和从相遇交点出发都同时到环的入口处
* assumption: input: head; output: node; null/empty: None;

## Solution:

```text
class Solution(object):
    def listCycle(self, head):
        if not head:
            return None
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                break
            else:
                return None
        while head != slow:
            head = head.next
            slow = slow.next
        return head
```



