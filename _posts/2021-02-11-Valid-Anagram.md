---
layout:     post
title:      LeetCode 242 Valid Anagram (Python)
number:     242
level:      Easy
lcurl:      valid-anagram
youtube:    _HkLhzV_KjE
bilibili1:  //player.bilibili.com/player.html?aid=416673756&bvid=BV1hV411i73u&cid=296371567&page=1
xigua:      
date:       2021-02-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given two strings s and t , write a function to determine if t is an anagram of s.

### 解题思路

使用Counter统计两个字符串，判断是否相同

### 代码
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return Counter(s) == Counter(t)
```
