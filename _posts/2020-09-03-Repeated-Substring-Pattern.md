---
layout:     post
title:      LeetCode 459 Repeated Substring Pattern (Python)
number:     459
level:      Easy
lcurl:      repeated-substring-pattern
youtube:    
bilibili1:  
xigua:      
date:       2020-09-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

### 解题思路

如果该字符串符合条件，那么将其重复两次，并去掉两端的字符串，一定包含该字符串
```
设t = s + s，若s在t中的起始位置不为0或n，则符合条件，那么设这个起始位置为i (0<i<n),s[x:y]表示s的第x个字符到第y个字符
s[0: n - 1] = t[i: n + i - 1]
将t[i: n + i - 1]在n - 1位置分成两段
s[0: n - i - 1] = t[i: n - 1]
s[n - i: n - 1] = t[n: n + i - 1] = t[0: i - 1]

s[0: n - i - 1] = s[i: n - 1]
s[n - i: n - 1] = s[0: i - 1]
对于任意j，s[j % n] = s[(j + i) % n]
```

### 代码
```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        return (s + s).find(s, 1) != len(s)
```
