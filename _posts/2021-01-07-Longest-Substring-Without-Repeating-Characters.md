---
layout:     post
title:      LeetCode 3 Longest Substring Without Repeating Characters (Python)
number:     3
level:      Medium
lcurl:      longest-substring-without-repeating-characters
youtube:    
bilibili1:  
xigua:      
date:       2020-01-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string s, find the length of the longest substring without repeating characters.

### 解题思路



### 代码
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        tmp = {}
        start = res = 0
        for i, c in enumerate(s):
            if c in tmp and start <= tmp[c]:
                start = tmp[c] + 1
            else:
                res = max(res, i - start + 1)
            tmp[c] = i
        return res
```
