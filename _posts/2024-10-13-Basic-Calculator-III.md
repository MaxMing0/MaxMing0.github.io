---
layout:     post
title:      LeetCode 772 Basic Calculator III (Python)
number:     772
level:      Hard
lcurl:      
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目



### 解题思路

中缀转后缀表达式

### 代码
```python
# Not submit to LC as it locked
def infix_to_list(exp):
    cur = 0
    res = []
    for i, c in enumerate(exp):
        if c.isdigit():
            cur = cur * 10 + int(c)
        else:
            if cur > 0:
                res.append(str(cur))
                cur = 0
            res.append(c)
    if cur > 0:
        res.append(str(cur))
    return res

def priority(ch):
    if ch in "+-":
        return 0
    if ch in "*/":
        return 1
    return -1

def infix_to_suffix(exp):
    s1, s2 = [], []
    for item in exp:
        if item.isdigit():
            s2.append(item)
        elif item == '(':
            s1.append(item)
        elif item == ')':
            while s1[-1] != '(':
                s2.append(s1.pop())
            s1.pop()
        else:
            while s1 and priority(s1[-1]) >= priority(item):
                s2.append(s1.pop())
            s1.append(item)
    while s1:
        s2.append(s1.pop())
    return s2

def calculate(exp):
    s = []
    for item in exp:
        if item.isdigit():
            s.append(item)
        else:
            op2 = int(s.pop())
            op1 = int(s.pop())
            if item == '+':
                s.append(op1 + op2)
            elif item == '-':
                s.append(op1 - op2)
            elif item == '*':
                s.append(op1 * op2)
            else:
                s.append(op1 // op2)
    return s[-1]

exp = "1+((2+3)*4)-5"
list_exp = infix_to_list(exp)
suffix = infix_to_suffix(list_exp)
print(calculate(suffix))
```
