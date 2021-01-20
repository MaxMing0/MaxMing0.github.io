---
layout:     post
title:      LeetCode 5 Longest Palindromic Substring (Python)
number:     5
level:      Medium
lcurl:      longest-palindromic-substring
youtube:    9s5lFFomSOg
bilibili1:  //player.bilibili.com/player.html?aid=373708919&bvid=BV1so4y1o765&cid=284884615&page=1
xigua:      
date:       2021-01-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string s, return the longest palindromic substring in s.

### 解题思路

枚举回文字符串中间的位置，向两边进行拓展，如果剩余长度小于等于当前最优的一半，结束循环，同时可以跳过连续相同的字母，使他们一起作为回文字符串的中间部分

### 代码
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        l = len(s)
        if l < 2:
            return s
        i = st = maxl = 0
        while i < l:
            if l - i <= maxl / 2:
                break
            j = k = i
            while k < l - 1 and s[k + 1] == s[k]:
                k += 1
            i = k + 1
            while k < l - 1 and j > 0 and s[k + 1] == s[j - 1]:
                k += 1
                j -= 1
            tmp = k - j + 1
            if tmp > maxl:
                st = j
                maxl = tmp
        return s[st: st + maxl]
```
