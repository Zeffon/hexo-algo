---
layout: post
title: 234.回文链表
categories:
  - LeetCode
tags:
  - linked List
summary: 请判断一个链表是否为回文链表。
abbrlink: 368b4e07
---

### 题目要求
请判断一个链表是否为回文链表。

### 题目示例
**`示例 1:`**
```
输入: 1->2
输出: false
```

**`示例 2:`**
```
输入: 1->2->2->1
输出: true
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
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null) {
            return true;
        }

        ListNode slow = head, fast = head;
        while(fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        slow.next = reverse(slow.next);

        slow = slow.next;
        ListNode cur = head;
        while(slow != null) {
            if(cur.val != slow.val) {
                return false;
            } else {
                slow = slow.next;
                cur = cur.next;
            }
        }
        return true;
    }

    private ListNode reverse(ListNode head) {
        if(head == null || head.next == null) { 
            return head;
        }

        ListNode pre = head;
        ListNode cur = head.next;
        ListNode next = cur.next;
        head.next = null;

        while(true) {
            cur.next = pre;
            pre = cur;
            cur = next;
            if(cur == null) {
                break;
            }
            next = cur.next;
        }
        return pre;
    }
}
```

### 题目来源
LeetCode-[234.回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/)
