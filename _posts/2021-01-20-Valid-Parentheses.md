---
layout:     post
title:      LeetCode 20 Valid Parentheses (Python)
number:     20
level:      Easy
lcurl:      longest-palindromic-substring
youtube:    4baExEEug5c
bilibili1:  //player.bilibili.com/player.html?aid=756257070&bvid=BV1Hr4y1M7Sc&cid=285352411&page=1
xigua:      
date:       2021-01-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.

### 解题思路

使用栈，遇到左括号进栈，右括号则与栈顶元素判断是否能匹配，最后栈需要为空

### 代码
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        dic = {']':'[', ')':'(', '}':'{'}
        for c in s:
            if c not in dic:
                stack.append(c)
            else:
                if not stack or stack.pop() != dic[c]:
                    return False
        return stack == []
```
