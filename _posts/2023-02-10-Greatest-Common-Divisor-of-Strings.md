---
layout:     post
title:      LeetCode 1071 Greatest Common Divisor of Strings (Python)
number:     1071
level:      Easy
lcurl:      greatest-common-divisor-of-strings
youtube:    C9CfKjH8fgk
bilibili1:  
xigua:      
date:       2023-02-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

For two strings s and t, we say "t divides s" if and only if s = t + ... + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

### 解题思路

如果 `s1 + s2 != s2 + s1` 一定不存在答案，反之一定存在，对于存在的情况，结果为两个字符串长度的最大公约数

### 代码
```python
import math

class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if str1 + str2 != str2 + str1:
            return ""
        return str1[:math.gcd(len(str1), len(str2))]
```
