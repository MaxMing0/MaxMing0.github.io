---
layout:     post
title:      LeetCode 696 Count Binary Substrings (Python)
number:     696
level:      Easy
lcurl:      count-binary-substrings
youtube:    yHjl-Dazdzo
bilibili1:  //player.bilibili.com/player.html?aid=972764550&bvid=BV14p4y1b7nV&cid=328830661&page=1
xigua:      
date:       2021-04-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.

Substrings that occur multiple times are counted the number of times they occur.

### 解题思路

比较连续两段的长度，可以构成较短长度个符合要求的字符串，

### 代码
```python
class Solution:
    def countBinarySubstrings(self, s: str) -> int:
        pre, cur, res = 0, 1, 0
        for i in range(1, len(s)):
            if s[i] == s[i - 1]:
                cur += 1
            else:
                pre, cur = cur, 1
            if pre >= cur:
                res += 1
        return res
```
