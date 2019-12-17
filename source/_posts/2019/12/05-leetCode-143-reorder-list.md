---
layout: post
title: 143.重排链表
categories:
  - LeetCode
tags:
  - linked List
summary: 重新排列链表。
abbrlink: 1648e7be
---

### 题目要求
给定一个单链表 L：L0→L1→…→Ln-1→Ln ，
将其重新排列后变为： L0→Ln→L1→Ln-1→L2→Ln-2→…

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

### 题目示例
**`示例 1:`**
```
给定链表 1->2->3->4, 重新排列为 1->4->2->3.
```

**`示例 2:`**
```
给定链表 1->2->3->4->5, 重新排列为 1->5->2->4->3.
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
    public void reorderList(ListNode head) {
        if (head != null) {
            //找到链表中点。
            ListNode slow = head, fast = head;
            while (fast.next != null && fast.next.next != null) {
                slow = slow.next;
                fast = fast.next.next;
            }
            //断开后，逆转后半部分
            fast = slow.next;
            //从中间断开
            slow.next = null;
            ListNode pre = null, tmp = null;
            while (fast != null) {
                tmp = fast.next;
                fast.next = pre;

                pre = fast;
                fast = tmp;
            }
            //同时从两端遍历，向前半段中加入节点 slow, pre
            slow = head;
            while (pre != null) {
                tmp = slow.next;
                slow.next = pre;
                slow = slow.next;

                pre = pre.next;
                slow.next = tmp;
                slow = slow.next;
            }
        }  
    }
}
```

### 题目来源
LeetCode-[143.重排链表](https://leetcode-cn.com/problems/reorder-list/)
