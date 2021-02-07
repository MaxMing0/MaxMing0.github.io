---
layout:     post
title:      LeetCode 821 Shortest Distance to a Character (Python)
number:     821
level:      Easy
lcurl:      shortest-distance-to-a-character
youtube:    7EBeAa-qyqk
bilibili1:  //player.bilibili.com/player.html?aid=799049983&bvid=BV1gy4y1Y784&cid=294319064&page=1
xigua:      
date:       2021-02-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string s and a character c that occurs in s, return an array of integers answer where answer.length == s.length and answer[i] is the shortest distance from s[i] to the character c in s.

### 解题思路

先找出每个c出现的位置，同时遍历字符串和c出现的位置，找到距离最近的c

### 代码
```python
class Solution:
    def shortestToChar(self, s: str, c: str) -> List[int]:
        pos, res = [], []
        for i in range(len(s)):
            if s[i] == c:
                pos.append(i)
        p = 0
        for i in range(len(s)):
            if i < pos[0]:
                res.append(pos[0] - i)
            elif i > pos[-1]:
                res.append(i - pos[-1])
            elif i == pos[p]:
                res.append(0)
                p += 1
            else:
                res.append(min(pos[p] - i, i - pos[p - 1]))
        return res
```
