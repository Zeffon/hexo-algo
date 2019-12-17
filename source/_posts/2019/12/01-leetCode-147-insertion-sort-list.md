---
layout: post
title: 147.对链表进行插入排序
categories:
  - LeetCode
tags:
  - linked List
summary: 对链表进行插入排序。
abbrlink: 977ced29
---

### 题目要求
对链表进行插入排序。
插入排序的动画演示如上。从第一个元素开始，该链表可以被认为已经部分排序（用黑色表示）。
每次迭代时，从输入数据中移除一个元素（用红色表示），并原地将其插入到已排好序的链表中。

**插入排序算法：**
插入排序是迭代的，每次只移动一个元素，直到所有元素可以形成一个有序的输出列表。
每次迭代中，插入排序只从输入数据中移除一个待排序的元素，找到它在序列中适当的位置，并将其插入。
重复直到所有输入数据插入完为止。

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
    public ListNode insertionSortList(ListNode head) {
        if(head == null || head.next == null) {
            return head;
        }

        ListNode dummyHead = new ListNode(0);
        dummyHead.next = head;

        ListNode pre = dummyHead.next;
        while(pre.next != null) {
            int val = pre.next.val;
            ListNode next = pre.next.next;
            ListNode pi = dummyHead;
            for(; pi != pre; pi = pi.next) {
                if(pi.next.val > val) {
                    ListNode pj = pi.next;
                    ListNode swapNode = pre.next;

                    pi.next = swapNode;
                    swapNode.next = pj;
                    pre.next = next;
                    break;
                }
            }
            if(pi == pre) {
                pre = pre.next;
            }
        }
        return dummyHead.next;
    }
}
```

### 题目来源
LeetCode-[147.对链表进行插入排序](https://leetcode-cn.com/problems/insertion-sort-list/)
