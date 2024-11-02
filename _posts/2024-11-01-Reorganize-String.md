---
layout:     post
title:      LeetCode 767 Reorganize String (Python)
number:     767
level:      Medium
lcurl:      reorganize-string
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a string s, rearrange the characters of s so that any two adjacent characters are not the same.

Return any possible rearrangement of s or return "" if not possible.

### 解题思路

用counter求出每个字符出现的次数，如果最多出现的字符超过一半，则无法符合要求。否则按照字母出现的次数，从多到少，先填偶数位再填奇数位

### 代码
```python
class Solution:
    def reorganizeString(self, s: str) -> str:
        n = len(s)
        ct = Counter(s)
        if max(ct.values()) > (n + 1) // 2:
            return ""
        res = [""] * n
        i = 0
        for k, v in ct.most_common():
            for j in range(v):
                res[i] = k
                i += 2
                if i >= n:
                    i = 1
        return "".join(res)
```
