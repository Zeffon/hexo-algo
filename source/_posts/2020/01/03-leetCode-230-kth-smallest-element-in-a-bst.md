---
layout: post
title: 230.二叉搜索树中第K小的元素
categories:
  - LeetCode
tags:
  - binary Search Tree
abbrlink: e7a72fb5
date: 2020-01-03 13:11:29
---

### 题目要求
给定一个二叉搜索树，编写一个函数 kthSmallest 来查找其中第 k 个最小的元素。

<!-- more -->

- **`说明:`**
你可以假设 k 总是有效的，1 ≤ k ≤ 二叉搜索树元素个数。


- **`进阶：`**
如果二叉搜索树经常被修改（插入/删除操作）并且你需要频繁地查找第 k 小的值，你将如何优化 kthSmallest 函数？

### 题目示例
- **`示例 1:`**
```
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 1
```

- **`示例 2:`**
```
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 3
```


### 解题思路
递归查找k元素，借助于index

### 解题代码
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    // 标记k的计数器，当k == index 则表示找到该元素
    private int index;

    public int kthSmallest(TreeNode root, int k) {
        index = 0;
        return kthSmallestNode(root, k).val;
    }

    // 寻找到k对应的节点
    private TreeNode kthSmallestNode(TreeNode node, int k) {
        if(node == null) {
            return null;
        }
        TreeNode res = kthSmallestNode(node.left, k);
        if(res != null) {
            return res;
        } 

        index++;
        if(index == k) {
            return node;
        }
        return kthSmallestNode(node.right, k);
    } 
}
```

### 题目来源
LeetCode-[230.二叉搜索树中第K小的元素](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/)
