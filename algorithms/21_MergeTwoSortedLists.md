## Problem

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example**
```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

## Solution 1
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
```

## Solution 2
首先想到需要使用临时区来保存新合并后的链表，想到可以采用链表尾插法来构造新链表。

**非递归实现:**
```java
public class MergeTwoList {
    public static class ListNode {
        int value;
        ListNode next;
        ListNode (int x){value=x;}

    }

    public static ListNode mergeList(ListNode l1, ListNode l2) {
        if (l1 == null && l2 == null) {
            return null;
        }
        ListNode root = new ListNode();
        //pointer始终指向新链表的尾部
        ListNode pointer = root;
        //两个有序链表逐个元素判断直至两个链表中其中一个为空
        while (l1 != null && l2 != null) {
            if (l1.value < l2.value) {
                pointer.next = l1;
                l1=l1.next;
            } else {
                pointer.next = l2;
                l2=l2.next;
            }
            pointer=pointer.next;
        }
        //如果其中一个不为空则补充到新链表尾节点后
        if (l1 != null) {
            pointer.next = l1;

        }
        if (l2 != null) {
            pointer.next = l2;

        }
        return root.next;
    }

    public static void printList(ListNode head) {
        while (head != null) {
            System.out.print(head.value + "->");
            head = head.next;
        }
        System.out.println("null");
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);
        ListNode head2 = new ListNode(1);
        head2.next = new ListNode(3);
        head2.next.next = new ListNode(5);
        head2.next.next.next = new ListNode(6);
        head2.next.next.next.next = new ListNode(7);
        head = mergeList(head, head2);
        //head = merge2(head, head2);
        printList(head);
    }
}
```

## Solution 3

**递归实现：**

```java
public static ListNode mergerList2(ListNode l1,ListNode l2){
    if(l1==null&&l2==null){
        return null;
    }
    if(l1==null){
        return l2;
    }
    if(l2==null){
        return l1;
    }
    if(l1.value<l2.value){
        l1.next=mergerList2(l1.next,l2);
        return l1;
    }else{
        l2.next=mergerList2(l1,l2.next);
        return l2;
    }
}
```

link: https://leetcode.com/problems/merge-two-sorted-lists/

