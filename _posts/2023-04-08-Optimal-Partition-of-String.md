---
layout:     post
title:      LeetCode 2405 Optimal Partition of String (Python)
number:     2405
level:      Medium
lcurl:      optimal-partition-of-string
youtube:    jrYQ8jPhrxY
bilibili1:  
xigua:      
date:       2023-04-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Given a string s, partition the string into one or more substrings such that the characters in each substring are unique. That is, no letter appears in a single substring more than once.

Return the minimum number of substrings in such a partition.

Note that each character should belong to exactly one substring in a partition.

### 解题思路

贪心，让每个字符串尽可能多包含字母的个数，如果出现重复的字母就进行分割

### 代码
```python
class Solution:
    def partitionString(self, s: str) -> int:
        res, seen = 1, ""
        for c in s:
            if c in seen:
                seen = c
                res += 1
            seen += c
        return res
```
