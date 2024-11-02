---
layout:     post
title:      LeetCode 680 Valid Palindrome II (Python)
number:     680
level:      Easy
lcurl:      valid-palindrome-ii
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

Given a string s, return true if the s can be palindrome after deleting at most one character from it.

### 解题思路

从左右两端判断是否为回文，当不是的时候，从左右各删除一个字符，判断是不是

### 代码
```python
class Solution:
    def validPalindrome(self, s: str) -> bool:
        if s == s[::-1]:
            return True
        i, j = 0, len(s) - 1
        while i < j:
            if s[i] == s[j]:
                i += 1
                j -= 1
                continue
            p = s[:i] + s[i + 1:]
            q = s[:j] + s[j + 1:]
            return p == p[::-1] or q == q[::-1]
```
