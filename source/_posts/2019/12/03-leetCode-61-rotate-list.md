---
layout: post
title: 61.旋转链表
categories:
  - LeetCode
tags:
  - linked List
summary: 给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。
abbrlink: d11874bc
---

### 题目要求
给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

### 题目示例
**`示例 1:`**
```
输入: 1->2->3->4->5->NULL, k = 2
输出: 4->5->1->2->3->NULL
解释:
向右旋转 1 步: 5->1->2->3->4->NULL
向右旋转 2 步: 4->5->1->2->3->NULL
```

**`示例 2:`**
```
输入: 0->1->2->NULL, k = 4
输出: 2->0->1->NULL
解释:
向右旋转 1 步: 2->0->1->NULL
向右旋转 2 步: 1->2->0->NULL
向右旋转 3 步: 0->1->2->NULL
向右旋转 4 步: 2->0->1->NULL
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
    public ListNode rotateRight(ListNode head, int k) {
        if(head == null) {
            return null;
        }
        int len = get_len(head);
        k = k % len;

        ListNode end = head;
        for(int i = 0; i < k; i++) {
            end = end.next;
        }

        ListNode start = head;
        while(end.next != null) {
            start = start.next;
            end = end.next;
        }

        end.next = head;
        head = start.next;
        start.next = null;

        return head;
    }
    private int get_len(ListNode head) {
        int res = 0;
        while(head != null) {
            res++;
            head = head.next;
        }
        return res;
    }
}
```

### 题目来源
LeetCode-[61.旋转链表](https://leetcode-cn.com/problems/rotate-list/)
