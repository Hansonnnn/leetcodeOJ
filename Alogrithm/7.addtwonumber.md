#### Add two number

>Question:给出两链表，进行类似数学加法计算。

>Example:
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)

Output: 7 -> 0 -> 8

>程序开始设立一个节点为0 的链表，并再设立一个指向他的节点，方便以后next。这是一大技巧。
程序后面还要注意的加法进位以及是否一个数已经计算完毕，但后面还有位数的可能性。

```
int flag = 0;
ListNode list1 = new ListNode(0);
ListNode list2 = new ListNode(0);

public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    addTwoNode(l1, l2);
    return l1;

}
public ListNode addTwoNode(ListNode l1, ListNode l2) {
    int sum = l1.val + l2.val + flag;
    l1.val = sum % 10;
    flag = sum / 10;
    if (l1.next != null && l2.next != null) {
        addTwoNode(l1.next, l2.next);
    } else if (l1.next == null && l2.next == null) {
        if (flag == 1) {
            ListNode tmp = new ListNode(1);
            l1.next = tmp;
            flag = 1;
        }
    } else if (l1.next != null && l2.next == null) {
        list1 = addTwoNode(l1.next, list2);
        l1.next = list1;
    } else if (l1.next == null && l2.next != null) {
        list1 = addTwoNode(l2.next, list2);
        l1.next = list1;
    }
    return l1;
}
