---
layout:     post
title:      LeetCode 32 Longest Valid Parentheses (Python)
number:     32
level:      Hard
lcurl:      longest-valid-parentheses
youtube:    TTWU77-WTbU
bilibili1:  //player.bilibili.com/player.html?aid=374880052&bvid=BV1RZ4y1F7nJ&cid=319421562&page=1
xigua:      
date:       2021-04-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.

### 解题思路

使用栈，栈存坐标，栈底元素为最后一个没被匹配的右括号，遇到左括号进栈，遇到右括号出栈，并更新结果（如果栈为空，则这个是最后一个没被匹配的右括号）

### 代码
```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        stack = [-1]
        res = 0
        for i, c in enumerate(s):
            if c == '(':
                stack.append(i)
            else:
                stack.pop()
                if not stack:
                    stack.append(i)
                else:
                    res = max(res, i - stack[-1])
        return res
```
