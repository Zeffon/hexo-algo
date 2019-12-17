---
layout: post
title: 1239.串联字符串的最大长度
categories:
  - LeetCode
tags:
  - array
summary: 请返回所有可行解 s 中最长长度。
abbrlink: 281222d1
---

### 题目要求
给定一个字符串数组 arr，字符串 s 是将 arr 某一子序列字符串连接所得的字符串，如果 s 中的每一个字符都只出现过一次，那么它就是一个可行解。

请返回所有可行解 s 中最长长度。

- **`提示`：**
1. 1 <= arr.length <= 16
1. 1 <= arr[i].length <= 26
1. arr[i] 中只含有小写英文字母

### 题目示例
**`示例1:`**  
```
输入：arr = ["un","iq","ue"]
输出：4
解释：所有可能的串联组合是 "","un","iq","ue","uniq" 和 "ique"，最大长度为 4。
```

**`示例2:`**  
```
输入：arr = ["cha","r","act","ers"]
输出：6
解释：可能的解答有 "chaers" 和 "acters"。
```

**`示例3:`**  
```
输入：arr = ["abcdefghijklmnopqrstuvwxyz"]
输出：26
```


### 解题思路
回溯的思路


### 解题代码
```java
class Solution {

    private int ret;

    public int maxLength(List<String> arr) {
        dfs(arr, 0, new StringBuilder());
        return ret;
    }

    private void dfs(List<String> arr, int start, StringBuilder builder) {
        if (!match(builder)) {
            return;
        }
        ret = Math.max(ret, builder.length());
        int size = arr.size();
        for (int i = start; i < size; i++) {
            String s = arr.get(i);
            builder.append(s);
            dfs(arr, i + 1, builder);
            builder.delete(builder.length() - s.length(), builder.length());
        }
    }

    private boolean match(StringBuilder builder) {
        String s = builder.toString();
        int[] count = new int[26];
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            count[c - 97]++;
            if (count[c - 97] > 1) {
                return false;
            }
        }
        return true;
    }
}
```

### 题目来源
LeetCode-[1239.串联字符串的最大长度](https://leetcode-cn.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/)
