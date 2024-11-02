---
layout:     post
title:      LeetCode 76 Minimum Window Substring (Python)
number:     76
level:      Hard
lcurl:      minimum-window-substring
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashMap
---

### 题目

Given two strings s and t of lengths m and n respectively, return the minimum window 
substring
 of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.

### 解题思路

用一个Counter存每个字母所需的个数，使用滑动窗口，当不缺所有的字符的时候，求出窗口的长度，之后如果满足条件就移动左边指针，否则移动右边指针，扫描整个字符串

### 代码
```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        i = j = I = J = 0
        miss = len(t)
        need = Counter(t)
        for c in s:
            if need[c] > 0:
                miss -= 1
            need[c] -= 1
            j += 1
            if miss == 0:
                while i < j and need[s[i]] < 0:
                    need[s[i]] += 1
                    i += 1
                if J == 0 or j - i < J - I:
                    I, J = i, j
        return s[I:J]
```
