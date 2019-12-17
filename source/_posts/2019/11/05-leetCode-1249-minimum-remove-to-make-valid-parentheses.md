---
layout: post
title: 1249.移除无效的括号
categories:
  - LeetCode
tags:
  - array
summary: 给你一个由 '('、')' 和小写字母组成的字符串 s。
abbrlink: f543bed6
---

### 题目要求
给你一个由 '('、')' 和小写字母组成的字符串 s。

你需要从字符串中删除最少数目的 '(' 或者 ')' （可以删除任意位置的括号)，使得剩下的「括号字符串」有效。

请返回任意一个合法字符串。

有效「括号字符串」应当符合以下 任意一条 要求：

空字符串或只包含小写字母的字符串
可以被写作 AB（A 连接 B）的字符串，其中 A 和 B 都是有效「括号字符串」
可以被写作 (A) 的字符串，其中 A 是一个有效的「括号字符串」


- **`提示`：**
1. 1 <= s.length <= 10^5
1. s[i] 可能是 '('、')' 或英文小写字母

### 题目示例
**`示例1:`**  
```
输入：s = "lee(t(c)o)de)"
输出："lee(t(c)o)de"
解释："lee(t(co)de)" , "lee(t(c)ode)" 也是一个可行答案。
```

**`示例2:`**  
```
输入：s = "a)b(c)d"
输出："ab(c)d"。
```

**`示例3:`**  
```
输入：s = "))(("
输出：""
解释：空字符串也是有效的6
```

**`示例4:`**  
```
输入：s = "(a(b(c)d)"
输出："a(b(c)d)"
```


### 解题思路
借助于栈
1. 转化成char数组
1. 遍历char数组，判断当前元素为`(`直接入栈;判断`当前`元素为`)`并且当前栈为空，把`)`替换成' '，否则将`栈顶`元素出栈
1. 遍历栈，将栈中的`所有元素`都替换成' '
1. 将操作后的字符重新`拼成`String，再将' '全部`替换`成""。

### 解题代码
```java
class Solution {
    public String minRemoveToMakeValid(String s) {
        Stack<Integer> stack = new Stack<>();
        char[] ch = s.toCharArray();
        for(int i = 0; i < ch.length; i++){
           if(ch[i] == '(')
                stack.push(i); 
            if(ch[i] == ')'){
                if(stack.empty())
                    ch[i] = ' ';
                else
                    stack.pop();
            }
        }

        while(!stack.empty())
            ch[stack.pop()] = ' ';
        String ret = new String(ch);
        ret = ret.replaceAll(" ","");
        
        return ret;
    }
}
```

### 题目来源
LeetCode-[1249.移除无效的括号](https://leetcode-cn.com/problems/minimum-remove-to-make-valid-parentheses/)
