# 22：链表中倒数第k个结点（19）

## Question:

输入一个链表，输出该链表中倒数第k个结点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾结点是倒数第1个结点。例如一个链表有6个结点，从头结点开始它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个结点是值为4的结点。

## Thought:

* Two passes：先遍历一遍链表，找出链表的长度，再遍历一遍直到**找到第 n-k+1 个节点**。
* One pass: two pointers 第一个指针先走 k-1 步，从第 k-1 步开始，第二个在指针从头遍历，直到第一个指针走到结尾。
* 拓展：求链表的中间节点。快指针走两步，慢指针走一步。
* **鲁棒性：头结点是空指针；链表长度小于k；k 为0.**

## Solution:

```text
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n (k): int
        :rtype: ListNode
        """
        if not head or n == 0:
            return None
        dummy = ListNode(0)
        dummy.next = head
        prev = dummy
        curr = dummy
        for _ in range(n): # traverse to the kth node
            if prev.next:
                prev = prev.next # if length of the list is smaller than k
            else:
                return None
        while prev and prev.next:
            curr = curr.next
            prev = prev.next
        curr.next = curr.next.next
        return dummy.next # return head
```



