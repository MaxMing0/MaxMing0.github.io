---
layout:     post
title:      LeetCode 567 Permutation in String (Python)
number:     567
level:      Medium
lcurl:      permutation-in-string
youtube:    nKXeVLBnONs
bilibili1:  //player.bilibili.com/player.html?aid=840644206&bvid=BV1154y1X7qB&cid=192462365&page=1
xigua:      
date:       2020-05-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

### 解题思路

用sliding window扫描s2，把字符串放到一个计数器中，每次更新这个计数器并和p的计数器比较，如果相同就返回True

### 代码
```python
class Solution:
    def checkInclusion(self, p: str, s: str) -> bool:
        def f(c):
            return ord(c) - 97
        
        ct_s, ct_p = [0] * 26, [0] * 26
        for c in p:
            ct_p[f(c)] += 1
        l = len(p)
        for c in s[: l - 1]:
            ct_s[f(c)] += 1
        for i, c in enumerate(s[l - 1:]):
            ct_s[f(c)] += 1
            if ct_s == ct_p:
                return True
            ct_s[f(s[i])] -= 1
        return False
```
