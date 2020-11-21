---
layout:     post
title:      LeetCode 902 Numbers At Most N Given Digit Set (Python)
number:     902
level:      Hard
lcurl:      numbers-at-most-n-given-digit-set
youtube:    pBuDJ--OdvE
bilibili1:  //player.bilibili.com/player.html?aid=330252212&bvid=BV19A411j7Wf&cid=258195520&page=1
xigua:      
date:       2020-11-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
    - Math
---

### 题目

Given an array of digits, you can write numbers using each digits[i] as many times as we want.  For example, if digits = ['1','3','5'], we may write numbers such as '13', '551', and '1351315'.

Return the number of positive integers that can be generated that are less than or equal to a given integer n.

### 解题思路

小于N位数的数可以直接求出来

与N位数相等的数使用dp，dp[i]表示小于等于N中最后`len(n)-i`位数的合法数的个数，`N = 6789`时，dp[0], dp[1], dp[2], dp[3]分别表示小于等于 6789, 789, 89, 9 的合法数的个数

### 代码
```python
class Solution:
    def atMostNGivenDigitSet(self, digits: List[str], n: int) -> int:
        S = str(n)
        ls, ld = len(S), len(digits)
        dp = [0] * ls + [1]
        for i in range(ls - 1, -1, -1):
            for d in digits:
                if d < S[i]:
                    dp[i] += ld ** (ls - i - 1)
                elif d == S[i]:
                    dp[i] += dp[i+1]
        return dp[0] + sum(ld ** i for i in range(1, ls))
```
