---
layout: post
title: 328.奇偶链表
categories:
  - LeetCode
tags:
  - linked List
summary: 给定一个单链表，把所有的奇数节点和偶数节点分别排在一起。
abbrlink: ebadf57a
---

### 题目要求
给定一个单链表，把所有的奇数节点和偶数节点分别排在一起。请注意，这里的奇数节点和偶数节点指的是节点编号的奇偶性，而不是节点的值的奇偶性。

请尝试使用原地算法完成。你的算法的空间复杂度应为 O(1)，时间复杂度应为 O(nodes)，nodes 为节点总数。


**`说明:`**
应当保持奇数节点和偶数节点的相对顺序。
链表的第一个节点视为奇数节点，第二个节点视为偶数节点，以此类推。


### 题目示例
**`示例 1:`**
```
输入: 1->2->3->4->5->NULL
输出: 1->3->5->2->4->NULL
```

**`示例 2:`**
```
输入: 2->1->3->5->6->4->7->NULL 
输出: 2->3->6->7->1->5->4->NULL
```

### 解题思路
1. 创建两个链表，分别是奇数链表p1和偶数链表p2
1. 从i=1开始遍历head链表，分别记录p1和p2的链表
1. 最终p1.next指向p2即可


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
    public ListNode oddEvenList(ListNode head) {
        if(head == null || head.next == null || head.next.next == null)
            return head;
        
        ListNode dummyHead1 = new ListNode(0); 
        ListNode dummyHead2 = new ListNode(0); 
        ListNode p1 = dummyHead1;
        ListNode p2 = dummyHead2;
        int i = 1;

        while(head != null) {
            if(i % 2 != 0) {
                p1.next = head;
                head = head.next;
                p1 = p1.next;
                p1.next = null;
                i++;
            } else {
                p2.next = head;
                head = head.next;
                p2 = p2.next;
                p2.next = null;
                i++;
            }
        }

        p1.next = dummyHead2.next;
        ListNode ret = dummyHead1.next;
        return ret;
    }
}
```


### 题目来源
LeetCode-[328.奇偶链表](https://leetcode-cn.com/problems/odd-even-linked-list/)
