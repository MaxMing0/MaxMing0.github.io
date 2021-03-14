---
layout:     post
title:      LeetCode 823 Binary Trees With Factors (Python)
number:     823
level:      Medium
lcurl:      binary-trees-with-factors
youtube:    BSEja7vFSbQ
bilibili1:  //player.bilibili.com/player.html?aid=374606231&bvid=BV13Z4y1w7K9&cid=310050844&page=1
xigua:      
date:       2021-03-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given an array of unique integers, arr, where each integer arr[i] is strictly greater than 1.

We make a binary tree using these integers, and each number may be used for any number of times. Each non-leaf node's value should be equal to the product of the values of its children.

Return the number of binary trees we can make. The answer may be too large so return the answer modulo 10……9 + 7.

### 解题思路

dp[i]表示以i为根的树的个数
dp[i] = 1 + sum(dp[n] * dp[i // n]) if i / n is integet and i / n in arr
sum(dp[i] for i in arr) 为所求

### 代码
```python
class Solution:
    def numFactoredBinaryTrees(self, arr: List[int]) -> int:
        MOD = 10**9 + 7
        arr = set(arr)
        @lru_cache(None)
        def dp(i):
            res = 1
            for n in arr:
                if i % n == 0 and i // n in arr:
                    res += dp(n) * dp(i // n)
            return res
        return sum(dp(i) for i in arr) % MOD
```
