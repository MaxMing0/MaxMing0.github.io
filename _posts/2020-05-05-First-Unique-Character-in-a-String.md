---
layout:     post
title:      LeetCode 387 First Unique Character in a String (Python)
number:     387
level:      Easy
lcurl:      first-unique-character-in-a-string
youtube:    FOZ4zkXnKD4
bilibili1:  //player.bilibili.com/player.html?aid=455549342&bvid=BV1b541147WU&cid=187319541&page=1
xigua:      
date:       
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

### 解题思路

将字符串转换成计数器，从头开始遍历字符串找到第一个只出现一次的字母，找不到返回`-1`

### 代码
```python
from collections import Counter
class Solution:
    def firstUniqChar(self, s: str) -> int:
        ct = Counter(s)
        for i, c in enumerate(s):
            if ct[c] == 1:
                return i
        return -1
```
