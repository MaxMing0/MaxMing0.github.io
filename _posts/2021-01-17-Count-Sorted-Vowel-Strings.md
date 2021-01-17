---
layout:     post
title:      LeetCode 1641 Count Sorted Vowel Strings (Python)
number:     1641
level:      Medium
lcurl:      count-sorted-vowel-strings
youtube:    zHt8CC2Hxwg
bilibili1:  //player.bilibili.com/player.html?aid=288692696&bvid=BV1jf4y1k7bJ&cid=283877102&page=1
xigua:      
date:       2021-01-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an integer n, return the number of strings of length n that consist only of vowels (a, e, i, o, u) and are lexicographically sorted.

A string s is lexicographically sorted if for all valid i, s[i] is the same as or comes before s[i+1] in the alphabet.

### 解题思路

排列组合问题，相当于把n个小球，分成5个部分，一共有多少分法

### 代码
```python
class Solution:
    def countVowelStrings(self, n: int) -> int:
        return math.comb(n + 4, 4)
```
