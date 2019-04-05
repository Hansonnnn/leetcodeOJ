## Problem
Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Example**
```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```

## Solution
```
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def mergeKLists(self, lists):
        vals = []
        first = point = ListNode(0)
        for l in lists:
            while l:
                vals.append(l.val)
                l = l.next
        for x in sorted(vals):
            node = ListNode(x)
            point.next = node
            point = point.next
        return first.next
```

link: https://leetcode.com/problems/merge-k-sorted-lists/

