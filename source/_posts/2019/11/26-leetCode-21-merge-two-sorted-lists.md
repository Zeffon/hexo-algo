---
layout: post
title: 21.合并两个有序链表
categories:
  - LeetCode
tags:
  - linked List
summary: 将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。
abbrlink: afbd1d19
---

### 题目要求
将两个有序链表合并为一个新的`有序`链表并返回。新链表是通过`拼接`给定的两个链表的`所有`节点组成的。

### 题目示例
**`示例:`**
```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode cur = dummyHead;
    
        while(l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                cur.next = l1;
                l1 = l1.next;
            } else {
                cur.next = l2;
                l2 = l2.next;
            }
            cur = cur.next;
        }
        if(l1 == null) {
            cur.next = l2;
        } else {
            cur.next = l1;
        }
        
        ListNode ret = dummyHead.next;
        return ret;
    }
}
```

### 题目来源
LeetCode-[21.合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)
