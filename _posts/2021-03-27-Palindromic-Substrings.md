---
layout:     post
title:      LeetCode 647 Palindromic Substrings (Python)
number:     647
level:      Medium
lcurl:      palindromic-substrings
youtube:    6k78G8uf0YI
bilibili1:  //player.bilibili.com/player.html?aid=844856415&bvid=BV1g54y1h7uv&cid=316162395&page=1
xigua:      
date:       2021-03-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

### 解题思路

枚举回文串的中点（同时枚举奇数偶数长度），向两边拓展

### 代码
```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        res = 0
        l = len(s)
        for mid in range(l * 2 - 1):
            left = mid // 2
            right = left + mid % 2
            while left >= 0 and right < l and s[left] == s[right]:
                res += 1
                left -= 1
                right += 1
        return res
```
