---
layout: post
title: 145.二叉树后序遍历
categories:
  - LeetCode
tags:
  - stack
  - binary Search Tree
summary: 给定一个二叉树，返回其节点值的后序遍历。
abbrlink: '856309e3'
---

### 题目要求
给定一个二叉树，返回其节点值的后序遍历。

- **`进阶`** 
递归解决方案是微不足道的，可以迭代吗？

### 题目示例
- **`示例 1:`** 
```
Input: [1,null,2,3]
   1
    \
     2
    /
   3
Output: [3,2,1]
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
    public List<Integer> postorderTraversal(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<>();
        if(root == null) {
            return res;
        }

        Stack<TreeNode> stack = new Stack<>();
        TreeNode pre = null;
        TreeNode cur = root;

        while(cur != null || !stack.isEmpty()) {
            if(cur != null) {
                stack.push(cur);
                cur = cur.left;
            } else {
                cur = stack.pop();
                if(cur.right == null || pre == cur.right){
                    res.add(cur.val);
                    pre = cur;
                    cur = null;
                }
                else{
                    stack.push(cur);
                    cur = cur.right;
                }
            }
        }
        return res;
    }
}
```

### 题目来源
LeetCode-[145.二叉树后序遍历](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/)
