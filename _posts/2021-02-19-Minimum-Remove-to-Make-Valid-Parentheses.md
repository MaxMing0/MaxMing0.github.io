---
layout:     post
title:      LeetCode 1249 Minimum Remove to Make Valid Parentheses (Python)
number:     1249
level:      Medium
lcurl:      minimum-remove-to-make-valid-parentheses
youtube:    CfHk-lovUB8
bilibili1:  //player.bilibili.com/player.html?aid=929277970&bvid=BV1wK4y1X7G7&cid=300445166&page=1
xigua:      
date:       2021-02-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string s of '(' , ')' and lowercase English characters. 

Your task is to remove the minimum number of parentheses ( '(' or ')', in any positions ) so that the resulting parentheses string is valid and return any valid string.

Formally, a parentheses string is valid if and only if:

- It is the empty string, contains only lowercase characters, or
- It can be written as AB (A concatenated with B), where A and B are valid strings, or
- It can be written as (A), where A is a valid string.

### 解题思路

遍历字符串，记录左括号的次数，遇到右括号减一，额外的右括号直接去除，如果最后有额外的左括号，从后向前去掉

### 代码
```python
class Solution:
    def minRemoveToMakeValid(self, s: str) -> str:
        ct = 0
        res = []
        for c in s:
            if c == '(':
                ct += 1
                res.append(c)
            elif c == ')':
                if ct > 0:
                    ct -= 1
                    res.append(c)
            else:
                res.append(c)
        for i in range(len(res)-1, -1, -1):
            if ct == 0:
                break
            if res[i] == "(":
                ct -= 1
                res[i] = ""
        return ''.join(res)
```
