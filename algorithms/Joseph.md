## 约瑟夫问题

提出问题，如果想要当选领导人，一开始应该站在那个位置？
假设有N个人，提出了以下的解决方案，所有人排成一个圆圈，按顺序数数，每隔第M个人退出圆圈，然后，其旁边的两个人会靠拢重新排成一个圆圈，这样依次下去，最后圆圈中只会剩下一个人，也就选出了领导人，也就是一开始应该所在的位置。而这一问题也就引出了数学上的一个问题——`约瑟夫`

>约瑟夫问题（有时也称为约瑟夫斯置换，是一个出现在计算机科学和数学中的问题。在计算机编程的算法中，类似问题又称为约瑟夫环。又称“丢手绢问题”.）

实现约瑟夫问题最简单的方法就是模拟循环链表来解决类似问题。

以下是java版本的约瑟夫问题实现，这里是构造了循环链表，然后指针自第一个节点开始每次向后移动M次，并且删除移动到第M次时指向的节点，依次下去，直至循环链表中只剩下一个节点。

```java
/**
 * Created by smith on 2017/3/28.
 * 约瑟夫问题
 * 循环链表，共N个节点，从第一个节点开始，每次删除第M个节点，直到只剩下一个节点
 */
public class Josephus {
    /**
     * 定义一个循环链表数据结构
     */

    public static class ListNode{
        int val;
        ListNode next;
        ListNode(int x){
            this.val=x;
        }

    }

    public static ListNode JosephusFunction(int m,int n){

         int i=2;int j;
         if(m==0||n==0||i>n){
             return null;
         }

        /**
         * 构造循环链表
         */
         ListNode node=null;
         ListNode root=new ListNode(1);
         ListNode head=root;

         while(i<=n){
             node=new ListNode(i);
             head.next=node;
             node.next=root;
             i++;
             head=node;
         }
         /**解决约瑟夫问题**/
        while(head!=head.next){
        for(j=1;j<m;j++){
            head=head.next;

         }
            head.next=head.next.next;
            n--;
        }
        return head;

    }
```

