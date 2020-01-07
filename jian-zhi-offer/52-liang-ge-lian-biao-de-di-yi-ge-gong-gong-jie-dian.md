# 52：两个链表的第一个公共结点 \(160\)

## Question:

输入两个链表，找出它们的第一个公共结点。

## Thought:

* stack, 从链表的尾部开始遍历，跟从尾到头打印链表一样
* 求链表的长度，先遍历长的再遍历短的；以上两种都是为了同时到达交点
*  **可以不用求长度：W**hen pApA reaches the end of a list, then redirect it to the head of B \(yes, B, that's right.\); similarly when pBpB reaches the end of a list, redirect it the head of A.

## Solution:

```text
class Solution(object):
    def getIntersectionNode(self, headA, headB):
        if not headA or not headB:
            return None
        # traverse to know length of two linked lists
        pa = headA
        lena = 0
        pb = headB
        lenb = 0
        while pa:
            lena += 1
            pa = pa.next
        while pb:
            lenb += 1
            pb = pb.next
        pa = headA
        pb = headB
        len_diff = abs(lenb - lena)
        if lenb > lena:
            while len_diff > 0:
                pb = pb.next
                len_diff -= 1
        else:
            while len_diff > 0:
                pa = pa.next
                len_diff -= 1
        while pa != pb:
            pa = pa.next
            pb = pb.next
        return pa
        #-------------------------
        pa = headA
        pb = headB
        while pa != pb:
            pa = headB if not pa else pa.next
            pb = headA if not pb else pb.next
        return pa   
```





