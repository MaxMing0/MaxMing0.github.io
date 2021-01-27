---
layout:     post
title:      LeetCode 1680 Concatenation of Consecutive Binary Numbers (Python)
number:     1680
level:      Medium
lcurl:      concatenation-of-consecutive-binary-numbers
youtube:    X0nHNgdBO14
bilibili1:  //player.bilibili.com/player.html?aid=798783967&bvid=BV1Py4y117o5&cid=288408911&page=1
xigua:      
date:       2021-01-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer n, return the decimal value of the binary string formed by concatenating the binary representations of 1 to n in order, modulo 10^9 + 7.

### 解题思路

遍历1到n，每次左移i的位数，并加i，之后取mod

### 代码
```python
class Solution:
    def concatenatedBinary(self, n: int) -> int:
        bits, res, MOD = 1, 0, 10**9 + 7
        for x in range(1, n + 1):
            res = ((res << bits) + x) % MOD
            if x == (1 << bits) - 1:
                bits += 1    
        return res
```
