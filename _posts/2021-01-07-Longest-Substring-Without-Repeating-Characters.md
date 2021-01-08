---
layout:     post
title:      LeetCode 3 Longest Substring Without Repeating Characters (Python)
number:     3
level:      Medium
lcurl:      longest-substring-without-repeating-characters
youtube:    -Dvp7xoFGO8
bilibili1:  //player.bilibili.com/player.html?aid=501010118&bvid=BV18K411M7d2&cid=279387767&page=1
xigua:      
date:       2020-01-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a string s, find the length of the longest substring without repeating characters.

### 解题思路

用一个指针表示子串开始的位置，使用一个字典存每个字符上次出现的位置，如果出现重复的，移动开始指针

### 代码
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        tmp = {}
        start = res = 0
        for i, c in enumerate(s):
            if c in tmp and start <= tmp[c]:
                start = tmp[c] + 1
            else:
                res = max(res, i - start + 1)
            tmp[c] = i
        return res
```
