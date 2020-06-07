---
layout:     post
title:      LeetCode 518 Coin Change 2 (Python)
number:     518
level:      Medium
lcurl:      Coin-Change-2
youtube:    WEqqrBjK00c
bilibili1:  //player.bilibili.com/player.html?aid=795943044&bvid=BV1jC4y1a7YT&cid=199646661&page=1
xigua:      
date:       2020-06-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

You are given coins of different denominations and a total amount of money. Write a function to compute the number of combinations that make up that amount. You may assume that you have infinite number of each kind of coin.

### 解题思路

dp[i][j]表示用前i种硬币，构造出j的组合数，dp[len(coins)][amount]为所求
```
dp[0][0] = 1
dp[0][i] = 0    1 <= i <= amount
dp[i][j] = dp[i - 1][j] + dp[i][j - coins[i]]
```

### 代码
```python
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        dp = [1] + [0] * amount
        for c in coins:
            for i in range(c, amount + 1):
                dp[i] += dp[i - c]
        return dp[amount]
```
