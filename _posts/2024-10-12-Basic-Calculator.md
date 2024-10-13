---
layout:     post
title:      LeetCode 224 Basic Calculator (Python)
number:     224
level:      Hard
lcurl:      basic-calculato
youtube:    
bilibili1:  
xigua:      
date:       2024-10-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - stack
---

### 题目

Given a string s representing a valid expression, implement a basic calculator to evaluate it, and return the result of the evaluation.

Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().

### 解题思路



### 代码
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack = []
        sign = 1
        res = cur = 0
        for c in s:
            if c.isdigit():
                cur = cur * 10 + int(c)
            else:
                res += cur * sign
                cur = 0
            if c == '+':
                sign = 1
            elif c == '-':
                sign = -1
            elif c == '(':
                stack.append(res)
                stack.append(sign)
                res = 0
                sign = 1
            elif c == ')':
                res += sign * cur
                res *= stack.pop()
                res += stack.pop()
                cur = 0
        return res + cur * sign
```
