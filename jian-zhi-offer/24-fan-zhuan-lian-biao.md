# 24：反转链表 \(206\)

## Question:

定义一个函数，输入一个链表的头结点，反转该链表并输出反转后链表的头结点。

## Thought:

* 迭代 \(从头到尾\)：当前节点的下一个节点要保存下来，不然当前节点改变方向之后，跟下一个节点就断了。
* 递归 \(从尾到头\)：Assume from node nk+1 to nm had been reversed and you are at node nk.

  n1 → … → nk-1 → **nk** → nk+1 ← … ← nm

  **We want nk+1’s next node to point to nk.**

  **So,**

  **nk.next.next = nk; 反转的时候，当前的node还是指向下一个node，要把箭头指向自己**

  Be very careful that n1's next must point to Ø. If you forget about this, your linked list has a cycle in it. This bug could be caught if you test your code with a linked list of size 2.

* 几个陷阱：表头为null； 翻转后链表出现断裂；返回的头结点不是原来的尾结点
* **善于用测试用例**：表头是null；只有一个节点；有多个节点
* [https://youtu.be/MRe3UsRadKw](https://youtu.be/MRe3UsRadKw) recursion

## Solution:

```text
class Solution(object):
    def reverseList(self, head):
    # iteration
        if not head or not head.next: # only have one node
            return head
        prev = None
        curr = head
        while curr:
            temp_next = curr.next # save the next node
            curr.next = prev # reverse this node
            prev = curr # turn to the next node
            curr = temp_next
        return prev # tail is the new head, head is null
    # recursion
        if not head or not head.next:
            return head
        curr = self.reverseList(head.next) # till the last node, it makes head as the last node
        head.next.next = head
        head.next = None # delet the connection and also prevent the first node from building a cycle
        return curr        
```

