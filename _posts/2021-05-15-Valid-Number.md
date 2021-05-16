---
layout:     post
title:      LeetCode 65 Valid Number (Python)
number:     65
level:      Hard
lcurl:      valid-number
youtube:    4_fmlrjMPk8
bilibili1:  //player.bilibili.com/player.html?aid=930612155&bvid=BV1hK4y1975b&cid=339220975&page=1
xigua:      
date:       2021-05-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

A valid number can be split up into these components (in order):

1. A decimal number or an integer.
2. (Optional) An 'e' or 'E', followed by an integer.
A decimal number can be split up into these components (in order):

1. (Optional) A sign character (either '+' or '-').
2. One of the following formats:
  1. At least one digit, followed by a dot '.'.
  2. At least one digit, followed by a dot '.', followed by at least one digit.
  3. A dot '.', followed by at least one digit.
An integer can be split up into these components (in order):

1. (Optional) A sign character (either '+' or '-').
2. At least one digit.
For example, all the following are valid numbers: ["2", "0089", "-0.1", "+3.14", "4.", "-.9", "2e10", "-90E3", "3e+7", "+6e-1", "53.5e93", "-123.456e789"], while the following are not valid numbers: ["abc", "1a", "1e", "e3", "99e2.5", "--6", "-+3", "95a54e53"].

Given a string s, return true if s is a valid number.

### 解题思路

使用正则表达式匹配

### 代码
```python
class Solution:
    def isNumber(self, s: str) -> bool:
        pattern = re.compile(r'^[+-]?(\d+|\d+\.\d*|\.\d+)([eE][+-]?\d+)?$')
        return pattern.match(s) is not None
```
