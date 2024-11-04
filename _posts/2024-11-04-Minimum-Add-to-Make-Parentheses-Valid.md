---
layout:     post
title:      LeetCode 921 Minimum Add to Make Parentheses Valid (Python)
number:     921
level:      Medium
lcurl:      minimum-add-to-make-parentheses-valid
youtube:    
bilibili1:  
xigua:      
date:       2024-11-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

A parentheses string is valid if and only if:

- It is the empty string,
- It can be written as AB (A concatenated with B), where A and B are valid strings, or
- It can be written as (A), where A is a valid string.
You are given a parentheses string s. In one move, you can insert a parenthesis at any position of the string.

- For example, if s = "()))", you can insert an opening parenthesis to be "(()))" or a closing parenthesis to be "())))".
Return the minimum number of moves required to make s valid.

### 解题思路

记录所需的右括号个数，如果遇到左括号，需要的个数+1，遇到右括号，如果需要则需要的-1，否则结果+1，最后结果加上所有的右括号个数

### 代码
```python
class Solution:
    def minAddToMakeValid(self, s: str) -> int:
        res = bal = 0
        for c in s:
            if c == "(":
                bal += 1
            elif bal:
                bal -= 1
            else:
                res += 1
        return res + bal
```
