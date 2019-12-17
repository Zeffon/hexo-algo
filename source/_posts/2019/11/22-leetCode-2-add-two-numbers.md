---
layout: post
title: 2.两数相加
categories:
  - LeetCode
tags:
  - linked List
summary: "给出两个\_非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照逆序的方式存储的，并且它们的每个节点只能存储一位数字。"
abbrlink: 1f082419
---

### 题目要求
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照`逆序`的方式存储的，并且它们的每个节点只能存储`一位`数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字`0`之外，这两个数都不会以0开头。



### 题目示例
**`示例:`**
```
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```


### 解题思路
```
 l1   2 -> 4 -> 3
  +
 l2   5 -> 6 -> 4
             +1
 ret  7 -> 0 -> 8
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode p1 = l1; 
        ListNode p2 = l2;
        ListNode dummyHead = new ListNode(0);
        ListNode cur = dummyHead;
        int carried = 0;
        while(p1 != null || p2 != null || carried != 0) {
            int a = p1 != null ? p1.val : 0;
            int b = p2 != null ? p2.val : 0;
            int sum = a + b + carried;
            cur.next = new ListNode(sum % 10);
            carried = sum / 10;
            
            cur = cur.next;
            p1 = p1 != null ? p1.next : null;
            p2 = p2 != null ? p2.next : null;
        }
                
        ListNode ret = dummyHead.next;
        return ret;
    }
}
```


### 题目来源
LeetCode-[2.两数相加](https://leetcode-cn.com/problems/add-two-numbers/)
