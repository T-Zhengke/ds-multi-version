# 划分链表

> 给你一个链表的头节点 head 和一个特定值 x ，请你对链表进行分隔，使得所有 小于 x 的节点都出现在 大于或等于 x 的节点之前。
> 
> 你应当 保留 两个分区中每个节点的初始相对位置。

```java

public ListNode partition(ListNode head, int x) {

    ListNode leftHead = null, leftTail = null;// <=x的区域
    ListNode rightHead = null, rightTail = null;// >=x的区域
    ListNode next = null;
    while (head != null) {
        next = head.next; // 保留现场
        head.next = null;

        if (head.val < x) {
            if (leftHead == null)
                leftHead = head;
            else
                leftTail.next = head;
            leftTail = head;
        } else {
            if (rightHead == null)
                rightHead = head;
            else
                rightTail.next = head;
            rightTail = head;
        }
        head = next;
    }
    // <=x的区域为空的情况
    if (leftHead == null)
        return rightHead;

    // <=x的区域不为空的情况
    leftTail.next = rightHead;
    return leftHead;
}
```