---
layout:     post
title:      LeetCode 91 Decode Ways (Python)
number:     91
level:      Medium
lcurl:      decode-ways
youtube:    1c6MaqqbM5k
bilibili1:  //player.bilibili.com/player.html?aid=292425957&bvid=BV1Pf4y1G7M5&cid=392258673&page=1
xigua:      
date:       2021-08-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

A message containing letters from A-Z can be encoded into numbers using the following mapping:
```
'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
```
To decode an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, "11106" can be mapped into:
```
"AAJF" with the grouping (1 1 10 6)
"KJF" with the grouping (11 10 6)
```
Note that the grouping (1 11 06) is invalid because "06" cannot be mapped into 'F' since "6" is different from "06".

Given a string s containing only digits, return the number of ways to decode it.

The answer is guaranteed to fit in a 32-bit integer.

### 解题思路

DP，设dp[i]表示前i个字符的种数, dp[n]为所求
```
dp[i] =   dp[i - 1] (s[i - 1] != 0) 
        + dp[i - 2] (i > 1, s[i - 2] != 0, s[i - 2: i] <= 26)
dp[0] = 1
```

### 代码
```python
class Solution:
    def numDecodings(self, s: str) -> int:
        n = len(s)
        dp0, dp1, dp2 = 0, 1, 0
        for i in range(1, n + 1):
            dp2 = 0
            if s[i - 1] != '0':
                dp2 += dp1
            if i > 1 and s[i - 2] != '0' and int(s[i - 2: i]) <= 26:
                dp2 += dp0
            dp0, dp1 = dp1, dp2
        return dp2
```
