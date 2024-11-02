---
layout:     post
title:      LeetCode 14 Longest Common Prefix (Python)
number:     14
level:      Easy
lcurl:      longest-common-prefix
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

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

### 解题思路

方法1，前两个字符串求最长公共前缀，结果和下一个字符串求，直到结束

方法2，对所有字符串排序，结果为第一和最后一个字符串的最长公共前缀

### 代码
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        def get_common_prefix(s1, s2):
            if len(s1) > len(s2):
                s1, s2 = s2, s1
            for i in range(len(s1)):
                if s1[i] != s2[i]:
                    return s1[:i]
            return s1

        if len(strs) == 0:
            return ""
        if len(strs) == 1:
            return strs[0]
        res = get_common_prefix(strs[0], strs[1])
        for s in strs[2:]:
            res = get_common_prefix(res, s)
        return res
```
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        def get_common_prefix(s1, s2):
            if len(s1) > len(s2):
                s1, s2 = s2, s1
            for i in range(len(s1)):
                if s1[i] != s2[i]:
                    return s1[:i]
            return s1

        strs = sorted(strs)
        return get_common_prefix(strs[0], strs[-1])
```
