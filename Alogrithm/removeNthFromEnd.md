##### Problem

Given a linked list, remove the n-th node from the end of list and return its head.

###### Example:
```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```
###### Note:

Given n will always be valid.

##### Solution
```
class ListNode:
    def __init__(self, x):
        self.x = x
        self.next = None


class Solution:
    def removeNthFromEnd(self, head, n):
        dummy = ListNode(0)
        dummy.next = head
        first = head
        length = 0
        while first is not None:
            length += 1
            first = first.next
        length -= n
        first = dummy
        while length > 0:
            length -= 1
            first = first.next
        first.next = first.next.next

        return dummy.next

