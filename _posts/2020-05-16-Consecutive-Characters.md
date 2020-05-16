---
layout:     post
title:      LeetCode 1446 Consecutive Characters (Python)
number:     1446
level:      Easy
lcurl:      consecutive-characters
youtube:    -axrGlGdPl8
bilibili1:  //player.bilibili.com/player.html?aid=968132371&bvid=BV1pp4y1Q7Rh&cid=191910508&page=1
xigua:      
date:       2020-05-16
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

遍历字符串，如果当前字符串与之前的不同，则更新结果，否则计数器+1，也可以使用`itertools.groupby`

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

import itertools
class Solution:
    def maxPower(self, s: str) -> int:
        return max(len(list(b)) for a, b in itertools.groupby(s))
```
