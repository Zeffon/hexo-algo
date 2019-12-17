---
layout: post
title: 445.两数相加 II
categories:
  - LeetCode
tags:
  - linked List
summary: 给定两个非空链表来代表两个非负整数。数字最高位位于链表开始位置。它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。
abbrlink: 92e554b5
---

### 题目要求
给定两个`非空`链表来代表两个非负整数。数字`最高位`位于链表开始位置。它们的每个节点只存储`单个`数字。将这两数相加会返回一个新的链表。

您可以假设除了数字`0`之外，这两个数都不会以0开头。


**`进阶:`**
如果输入链表不能修改该如何处理？换句话说，你不能对列表中的节点进行翻转。

### 题目示例
**`示例:`**
```
输入: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
输出: 7 -> 8 -> 0 -> 7
```


### 解题思路
1. 借助两个栈，将l1、l2中的元素每次添加进栈中的`第一位`。
1. 遍历两个栈，每次取出两个栈中的`栈顶`元素的值进行相加。
1. 确认最后一次相加之和有没有`超过9`。

**`逆着相加，因此每次入栈总是放在栈顶`**
```
l1   7 -> 2 -> 4 -> 3
+           +1
l2        5 -> 6 -> 4
=
ret  7 -> 8 -> 0 -> 7
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
        LinkedList<Integer> stack1 = new LinkedList<>();
        LinkedList<Integer> stack2 = new LinkedList<>();

        while(l1 != null) {
            stack1.addFirst(l1.val);
            l1 = l1.next;
        }

        while(l2 != null) {
            stack2.addFirst(l2.val);
            l2 = l2.next;
        }

        int carry = 0;
        ListNode ret = null;

        while(!stack1.isEmpty() || !stack2.isEmpty()) {
            int a = 0, b = 0;
            if(!stack1.isEmpty()) {
                a = stack1.removeFirst();
            }
            if(!stack2.isEmpty()) {
                b = stack2.removeFirst();
            }
            ListNode cur = new ListNode((a + b + carry) % 10);
            carry = (a + b + carry) / 10;
            cur.next = ret;
            ret = cur;
        }

        if(carry > 0) {
            ListNode cur = new ListNode(carry);
            cur.next = ret;
            ret = cur;
        }
        return ret;
    }
}
```


### 题目来源
LeetCode-[445.两数相加 II](https://leetcode-cn.com/problems/add-two-numbers-ii/)
