# linked list template

1. reverse linked list

```text
class Solution(object):
    def reverseList(self, head):
        # recursion
        if not head or not head.next:
            return head
        newhead = self.reverseList(head.next) # recurse til the end
        head.next.next = head # reverse the direction 
        head.next = None # cut the previous direction
        return newhead
    # ------------------------------------------
    # iteration
        prev = None
        curr = head
        while curr:
            next_temp = head.next
            head.next = prev
            prev = curr
            curr = next_temp
        return prev # new head
```

2. slow and fast node \(find cycles/ find middle node\)

```text
class Solution(object):
    def hasCycle(self, head):
        if not head or not head.next:
            return False
        slow = head
        fast = head.next # necessary
        while slow != fast:
            if not fast or not fast.next:
                return False
            slow = slow.next
            fast = fast.next.next
        return True
# --------------------------------------------------------
class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head:
            return None
        slow = fast = head
        while fast and fast.next: # pay attention to make sure fast exists
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                break
        else:
            return None
        while head != slow:
            slow = slow.next
            head = head.next
        return head
# -------------------------------------------------------------------------
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        if not head or not head.next:
            return True
        slow = head
        fast = head
        # find middle node
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        # reverse the second half of the linked list
        prev = None
        curr = slow
        while curr:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp
        # compare two parts of the linked list
        while prev:
            if prev.val != head.val:
                return False
            prev = prev.next
            head = head.next
        return True

```



