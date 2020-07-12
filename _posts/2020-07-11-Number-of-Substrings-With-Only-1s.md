---
layout:     post
title:      LeetCode 1513 Number of Substrings With Only 1s (Python)
number:     1513
level:      Medium
lcurl:      number-of-substrings-with-only-1s
youtube:    i89BiZI7l_I
bilibili1:  //player.bilibili.com/player.html?aid=286302441&bvid=BV1Vf4y1R7DG&cid=211612637&page=1
xigua:      
date:       2020-06-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a binary string s (a string consisting only of '0' and '1's).

Return the number of substrings with all characters 1's.

Since the answer may be too large, return it modulo 10^9 + 7.

### 解题思路

长度为n的连续的1可以构成 `n * (n + 1) / 2`子串

### 代码
```python
class Solution:
    def numSub(self, s: str) -> int:
        MOD = 1000000007
        res = ct = 0
        for i in range(len(s)):
            if s[i] == '0':
                res += (1 + ct) * ct // 2
                ct = 0
            else:
                ct += 1
        return (res + (1 + ct) * ct // 2) % MOD
```
