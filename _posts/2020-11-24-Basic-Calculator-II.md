---
layout:     post
title:      LeetCode 227 Basic Calculator II (Python)
number:     227
level:      Medium
lcurl:      basic-calculator-ii
youtube:    5E8udwGQt_k
bilibili1:  //player.bilibili.com/player.html?aid=797961772&bvid=BV1Qy4y167Ax&cid=259439474&page=1
xigua:      
date:       2020-11-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Implement a basic calculator to evaluate a simple expression string.

The expression string contains only non-negative integers, +, -, *, / operators and empty spaces . The integer division should truncate toward zero.

### 解题思路

使用栈，遇到加减法，直接把数加到栈中，乘除法需要先进行计算，将计算的结果再加入栈中

### 代码
```python
class Solution:
    def calculate(self, s: str) -> int:
        stack, cur, op = [], 0, '+'
        for c in s + '+':
            if c == " ":
                continue
            elif c.isdigit():
                cur = (cur * 10) + int(c)
            else:
                if op == '-':
                    stack.append(-cur)
                elif op == '+':
                    stack.append(cur)
                elif op == '*':
                    stack.append(stack.pop() * cur)
                elif op == '/':
                    stack.append(int(stack.pop() / cur))
                cur, op = 0, c
        return sum(stack)
```
