---
layout:     post
title:      LeetCode 322 Coin Change (Python)
number:     322
level:      Medium
lcurl:      coin-change
youtube:    QhmgpNXmZ2Q
bilibili1:  //player.bilibili.com/player.html?aid=799602277&bvid=BV1ty4y187dh&cid=309167631&page=1
xigua:      
date:       2021-03-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

### 解题思路

```
dp[i]表示组成i所需的最少硬币数
dp[i] = min(dp[i], dp[i-coin] + 1) for c in coins if i >= coin
dp[0] = 0
dp[n]为所求
```

### 代码
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        for coin in coins:
            for i in range(coin, amount + 1):
                dp[i] = min(dp[i], dp[i - coin] + 1)
        return dp[amount] if dp[amount] != float('inf') else -1
```
