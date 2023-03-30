---
layout:     post
title:      LeetCode 87 Scramble String (Python)
number:     87
level:      Hard
lcurl:      scramble-string
youtube:    HmOsxuBBRjE
bilibili1:  
xigua:      
date:       2023-03-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

We can scramble a string s to get a string t using the following algorithm:

If the length of the string is 1, stop.
If the length of the string is > 1, do the following:
- Split the string into two non-empty substrings at a random index, i.e., if the string is s, divide it to x and y where s = x + y.
- Randomly decide to swap the two substrings or to keep them in the same order. i.e., after this step, s may become s = x + y or s = y + x.
- Apply step 1 recursively on each of the two substrings x and y.
Given two strings s1 and s2 of the same length, return true if s2 is a scrambled string of s1, otherwise, return false.

### 解题思路

如果两个字符串是scramble，首先必须是由相同的字母构成，之后按照要求对字符串进行分割，递归判断两个字符串是否为scramble，记录每次递归的结果

### 代码
```python
from functools import cache
class Solution:
    def isScramble(self, s1: str, s2: str) -> bool:
        # dp = {}
        @cache
        def f(s1, s2):
            key = (s1, s2) if s1 < s2 else (s2, s1)
            # if key in dp:
            #     return dp[key]
            if sorted(s1) != sorted(s2):
                # dp[key] = False
                return False
            if len(s1) == 1:
                return True
            for i in range(1, len(s1)):
                if f(s1[:i], s2[:i]) and f(s1[i:], s2[i:]) or f(s1[:i], s2[-i:]) and f(s1[i:], s2[:-i]):
                    # dp[key] = True
                    return True
            # dp[key] = False
            return False

        return f(s1, s2)
```
