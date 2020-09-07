---
layout:     post
title:      LeetCode 290 Word Pattern (Python)
number:     290
level:      Easy
lcurl:      word-pattern
youtube:    DbL8c2Xg2eA
bilibili1:  //player.bilibili.com/player.html?aid=372112026&bvid=BV1HZ4y1N7wD&cid=233098854&page=1
xigua:      
date:       2020-09-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

### 解题思路

使用两个字典来存pattern到单词以及单词到pattern的映射，如果出现和之前不同的映射，则返回false

### 代码
```python
class Solution:
    def wordPattern(self, pattern: str, str: str) -> bool:
        str = str.split(" ")
        if len(pattern) != len(str):
            return False
        dic1, dic2 = {}, {}
        for p, w in zip(pattern, str):
            if p not in dic1:
                dic1[p] = w
            elif dic1[p] != w:
                return False
            if w not in dic2:
                dic2[w] = p
            elif dic2[w] != p:
                return False
        return True
```
