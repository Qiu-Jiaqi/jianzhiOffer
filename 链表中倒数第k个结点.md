## 题目描述

输入一个链表，输出该链表中倒数第k个结点。



## 题解

这题之前也做过，我记得当时一开始是只想到先遍历一次数个数的，两次遍历出结果，然而是可以双指针。

注意 while 循环里面要先写`pre != null`，不为 null 再对 k 减，若先减 k，当 k 刚好为链表长度 + 1 时出错。

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head, int k) {
        ListNode pre = head, cur = head;
        while (pre != null && k-- > 0) {
            pre = pre.next;
        }
        while (pre != null) {
            pre = pre.next;
            cur = cur.next;
        }
        return k > 0 ? null : cur;
    }
}
```

