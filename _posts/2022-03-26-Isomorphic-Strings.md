---
layout:     post
title:      LeetCode 205 Isomorphic Strings (Python)
number:     205
level:      Easy
lcurl:      isomorphic-strings
youtube:    GmKMof8j-u8
bilibili1:  
xigua:      
date:       2022-03-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

### 解题思路

使用一个字典，存字母之间的映射，使用一个集合维护在第二个字符串中所有出现过的字母，如果映射冲突，或者不同字母映射到的字母在集合中出现，则不是同构

### 代码
```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        chars = set()
        permutation = {}
        for i in range(0, len(s)):
            if s[i] not in permutation:
                if t[i] in chars:
                    return False
                else:
                    permutation[s[i]] = t[i]
                    chars.add(t[i])
            else:
                if t[i] != permutation[s[i]]:
                    return False
        return True
```
