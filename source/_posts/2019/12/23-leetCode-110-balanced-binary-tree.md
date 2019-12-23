---
layout: post
title: 110.平衡二叉树
categories:
  - LeetCode
tags:
  - binary Search Tree
summary: 给定一个二叉树，判断它是否是高度平衡的二叉树。
abbrlink: 3f648717
---

### 题目要求
给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：
> 一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。


### 题目示例
- **`示例 1:`**
给定二叉树 [3,9,20,null,null,15,7]
```
    3
   / \
  9  20
    /  \
   15   7
```
返回 true 。

- **`示例 2:`**
给定二叉树 [1,2,2,3,3,null,null,4,4]
```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```
返回 false 。


### 解题思路


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
    public boolean isBalanced(TreeNode root) {
        return depth(root) != -1;
    }

    public int depth(TreeNode root) {
        if(root == null) {
            return 0;
        }
        int left = depth(root.left);
        if(left == -1) {
            return -1;
        }
        int right = depth(root.right);
        if(right == -1) {
            return -1;
        }
        return Math.abs(left - right) < 2 ? Math.max(left, right) + 1 : -1;
    }
}
```



### 题目来源
LeetCode-[110.平衡二叉树](https://leetcode-cn.com/problems/balanced-binary-tree/)
