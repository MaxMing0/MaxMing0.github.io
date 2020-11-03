---
layout:     post
title:      LeetCode 1446 Consecutive Characters (Python)
number:     1446
level:      Easy
lcurl:      consecutive-characters
youtube:    _bHLlQwmscI
bilibili1:  //player.bilibili.com/player.html?aid=330241020&bvid=BV1QA411j7Qt&cid=252208858&page=1
xigua:      
date:       2020-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a string s, the power of the string is the maximum length of a non-empty substring that contains only one unique character.

Return the power of the string.

### 解题思路

遍历字符串，统计当前字符重复出现的次数，遇到新的字符从1开始

### 代码
```python
class Solution:
    def maxPower(self, s: str) -> int:
        res = ct = 1
        for i in range(1, len(s)):
            if s[i] != s[i - 1]:
                res = max(res, ct)
                ct = 1
            else:
                ct += 1
        return max(res, ct)
```
