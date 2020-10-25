---
layout:     post
title:      LeetCode 1510 Stone Game IV (Python)
number:     1510
level:      Hard
lcurl:      stone-game-iv
youtube:    AxRTy0UJ_rw
bilibili1:  
xigua:      
date:       2020-10-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Alice and Bob take turns playing a game, with Alice starting first.

Initially, there are n stones in a pile.  On each player's turn, that player makes a move consisting of removing any non-zero square number of stones in the pile.

Also, if a player cannot make a move, he/she loses the game.

Given a positive integer n. Return True if and only if Alice wins the game otherwise return False, assuming both players play optimally.

### 解题思路

dp, dp[i]=True表示先手赢，False表示先手输，`dp[0]=False`, `dp[i] = any(dp[i-j*j]=False) i >= j * j`

### 代码
```python
class Solution:
    def winnerSquareGame(self, n: int) -> bool:
        dp = [False] * (n + 1)
        for i in range(n + 1):
            j = 1
            while j * j <= i:
                if not dp[i - j * j]:
                    dp[i] = True
                    break
                j += 1
        return dp[n]
```
