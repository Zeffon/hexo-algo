---
layout: post
title: 83.删除排序链表中的重复元素
categories:
  - LeetCode
tags:
  - linked List
summary: 给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。
abbrlink: 2c538a68
---

### 题目要求
给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。


### 题目示例
**`示例 1:`**
```
输入: 1->1->2
输出: 1->2
```

**`示例 2:`**
```
输入: 1->1->2->3->3
输出: 1->2->3
```

### 解题思路
判断下一个节点的值是否等于当前节点的值，若是，将下一个节点进行跳过


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
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)
            return head;
        ListNode cur = head;
        while(cur != null) {
            ListNode next = cur.next;
            if(next != null && cur.val == next.val) {
                cur.next = next.next;
            } else {
                cur = cur.next;
            }
        }
        return head;
    }
}
```


### 题目来源
LeetCode-[83.删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)
