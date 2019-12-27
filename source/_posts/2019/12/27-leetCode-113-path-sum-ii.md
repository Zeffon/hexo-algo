---
layout: post
title: 113.路径总和 II
categories:
  - LeetCode
tags:
  - binary Search Tree
summary: 给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。
abbrlink: 1504ba16
---

### 题目要求
给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

- **`说明:`**
叶子节点是指没有子节点的节点。

### 题目示例
- **`示例:`**
给定如下二叉树，以及目标和 sum = 22，
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```
返回:
```
[
   [5,4,11,2],
   [5,8,4,5]
]
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
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> res = new ArrayList<>();
        if(root == null) {
            return res;
        }
        dfs(root, sum, res, new ArrayList<Integer>());
        return res;
    }

    private void dfs(TreeNode root, int sum, List<List<Integer>> res, ArrayList<Integer> tmp) {
        if (root == null) {
            return;
        }
        tmp.add(root.val);
        if (root.left == null && root.right == null && sum - root.val == 0) {
            res.add(new ArrayList<>(tmp));
        }
        dfs(root.left, sum - root.val, res, tmp);
        dfs(root.right, sum - root.val, res, tmp);
        tmp.remove(tmp.size() - 1);
    }
}
```

### 题目来源
LeetCode-[113.路径总和 II](https://leetcode-cn.com/problems/path-sum-ii/)
