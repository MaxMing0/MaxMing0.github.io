---
layout:     post
title:      LeetCode 451 Sort Characters By Frequency (Python)
number:     451
level:      Medium
lcurl:      sort-characters-by-frequency
youtube:    EhZlKElgdCo
bilibili1:  //player.bilibili.com/player.html?aid=243331302&bvid=BV18v411z7iy&cid=193890769&page=1
xigua:      
date:       2020-05-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a string, sort it in decreasing order based on the frequency of characters.

### 解题思路

使用一个计数器，然后按频率从大到小排序，再拼回去

### 代码
```python
from collections import Counter
class Solution:
    def frequencySort(self, s: str) -> str:
        return ''.join(k * v for k, v in sorted(Counter(s).items(), key=lambda x: x[1], reverse=True))
```
