##### Problem

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

###### Example
```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

##### Solution
```
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def mergeTwoLists(self, head1, head2):
        dummy = cur = ListNode(0)
        while head1 and head2:
            if head1.val < head2.val:
                cur.next = head1
                head1 = head1.next
            else:
                cur.next = head2
                head2 = head2.next
            cur = cur.next
        cur.next = head1 or head2
        return dummy.next


