---
layout: post
title: 25.K个一组翻转链表
categories:
  - LeetCode
tags:
  - linked List
summary: "给你一个链表，每\_k\_个节点一组进行翻转，请你返回翻转后的链表。"
abbrlink: 60ad993d
---

### 题目要求
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。


**`说明:`**
你的算法只能使用常数的额外空间。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

### 题目示例
**`示例:`**
```
给定这个链表：1->2->3->4->5
当 k = 2 时，应当返回: 2->1->4->3->5
当 k = 3 时，应当返回: 3->2->1->4->5
```

### 解题思路
```
   null -> 1 -> 2 -> 3 -> 4 -> 5
           |    
          pre

```


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
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode dummyHead = new ListNode(0);
        dummyHead.next = head;

        ListNode pre = dummyHead;

        while(pre != null && pre.next != null) {
            ListNode end = pre;
            int i;
            for(i = 0; i < k && end.next != null; i++) {
                end = end.next;
            }
            if(i != k) {
                break;
            }
                
            ListNode next = end.next;
            ListNode rhead = reverse(pre.next, end);

            ListNode tail = pre.next;
            pre.next = rhead;
            tail.next = next;
            pre = tail;
        }
        ListNode ret = dummyHead.next;
        return ret;
    }

    private ListNode reverse(ListNode head, ListNode end) {
        if(head == end) 
            return head;
        ListNode rhead = reverse(head.next, end);
        head.next.next = head;
        return rhead;
    }
}
```

### 题目来源
LeetCode-[25.K个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)
