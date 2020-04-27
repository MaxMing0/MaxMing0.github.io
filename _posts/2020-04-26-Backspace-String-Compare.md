---
layout:     post
title:      LeetCode 844 Backspace String Compare (Python)
number:     844
level:      Easy
lcurl:      backspace-string-compare
youtube:    BYbc-6WMvLk
bilibili1:  //player.bilibili.com/player.html?aid=795155027&bvid=BV1aC4y1s7LK&cid=176042609&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

### 解题思路



### 代码
```python
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        def build(s):
            s = list(s)
            i = 0
            for c in s:
                if c != '#':
                    s[i] = c
                    i += 1
                else:
                    if i:
                        i -= 1
            return ''.join(s[:i])
        return build(S) == build(T)
```