# 25：合并两个排序的链表 \(21\)

## Question:

输入两个递增排序的链表，合并这两个链表并使新链表中的结点仍然是按照递增排序的。

## Thought:

* 递归和迭代
* **在面试时先给出思路和举例说明**

## Solution:

```text
class Solution(object):
    def mergeList(self, l1, l2):
        # iterative
        dummy = ListNode(0)
        curr = dummy
        while l1 and l2:
            if l1.val < l2.val:
                curr.next = l1
                l1 = l1.next
            else:
                curr.next = l2
                l2 = l2.next
            curr = curr.next
        curr.next = l1 or l2 # add last node
        return dummy.next # still output dummy.next
        # recursion
        if not l1 or not l2:
            return l1 or l2
        if l1.val < l2.val:
            l1.next = self.mergeList(l1.next, l2)
            return l1 # return directly l1
        else:
            l2.next = self.mergeList(l1, l2.next)
            return l2 # return directly l2
```

