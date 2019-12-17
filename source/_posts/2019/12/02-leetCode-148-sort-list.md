---
layout: post
title: 148.排序链表
categories:
  - LeetCode
tags:
  - linked List
summary: 在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。
abbrlink: b80f3b8e
---

### 题目要求
在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。

### 题目示例
**`示例 1:`**
```
输入: 4->2->1->3
输出: 1->2->3->4
```

**`示例 2:`**
```
输入: -1->5->3->4->0
输出: -1->0->3->4->5
```

### 解题思路


### 解题代码
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode sortList(ListNode head) {
        if(head == null || head.next == null) {
            return head;
        }
        ListNode slow = head;
        ListNode fast = head.next;
        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }        
        ListNode head2 = slow.next;
        slow.next = null;
        head = sortList(head);
        head2 = sortList(head2);

        return merge(head, head2);
    }

    private ListNode merge(ListNode a, ListNode b) {
        ListNode dummyHead = new ListNode(0);
        ListNode p1 = a, p2 = b, p = dummyHead;
        while(p1 != null && p2 != null) {
            if(p1.val < p2.val) {
                p.next = p1;
                p1 = p1.next;
                p = p.next;
                p.next = null;
            } else {
                p.next = p2;
                p2 = p2.next;
                p = p.next;
                p.next = null;
            }
        }
        if(p1 != null) {
            p.next = p1;
        }
        if(p2 != null) {
            p.next = p2;
        }
        return dummyHead.next;
    }
}
```

### 题目来源
LeetCode-[148.排序链表](https://leetcode-cn.com/problems/sort-list/)
