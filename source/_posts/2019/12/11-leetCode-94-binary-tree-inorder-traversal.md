---
layout: post
title: 94. 二叉树的中序遍历
categories:
  - LeetCode
tags:
  - stack
  - binary Search Tree
summary: 给定一个二叉树，返回它的中序遍历。
abbrlink: 5b2d6749
---

### 题目要求
给定一个二叉树，返回它的中序遍历。

- **`进阶`** 
递归解决方案是微不足道的，可以迭代吗？

### 题目示例
- **`示例 1:`** 
```
输入: [1,null,2,3]
   1
    \
     2
    /
   3
输出: [1,3,2]
```


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
    public List<Integer> inorderTraversal(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<>();
        if(root == null) {
            return res;
        }

        Stack<TreeNode> stack = new Stack<>();
        TreeNode cur = root;
        while(cur != null || !stack.isEmpty()) {
            if(cur != null) {
                stack.push(cur);
                cur = cur.left;
            } else {
                cur = stack.pop();
                res.add(cur.val);
                cur = cur.right;
            }
        }
        return res; 
    }
}
```

### 题目来源
LeetCode-[94. 二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)
