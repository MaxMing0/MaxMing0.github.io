---
layout:     post
title:      LeetCode 438 Find All Anagrams in a String (Python)
number:     438
level:      Medium
lcurl:      find-all-anagrams-in-a-string
youtube:    OmgN9AqfxEk
bilibili1:  //player.bilibili.com/player.html?aid=840681600&bvid=BV1254y1X7HV&cid=192089342&page=1
xigua:      
date:       2020-05-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

### 解题思路

用sliding window扫描s，把字符串放到一个计数器中，每次更新这个计数器并和p的计数器比较，如果相同就是一个答案

### 代码
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        def f(c):
            return ord(c) - 97
    
        ct_p, ct_s = [0] * 26, [0] * 26
        for c in p:
            ct_p[f(c)] += 1
        l = len(p)
        for c in s[:l - 1]:
            ct_s[f(c)] += 1
        res = []
        for i, c in enumerate(s[l - 1:]):
            ct_s[f(c)] += 1
            if ct_s == ct_p:
                res.append(i)
            ct_s[f(s[i])] -= 1
        return res
```
