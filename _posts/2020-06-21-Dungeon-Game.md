---
layout:     post
title:      LeetCode 174 Dungeon Game (Python)
number:     174
level:      Hard
lcurl:      dungeon-game
youtube:    dJPy8txZopc
bilibili1:  //player.bilibili.com/player.html?aid=498578029&bvid=BV1TK411W7T1&cid=204447326&page=1
xigua:      
date:       2020-06-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

The demons had captured the princess (P) and imprisoned her in the bottom-right corner of a dungeon. The dungeon consists of M x N rooms laid out in a 2D grid. Our valiant knight (K) was initially positioned in the top-left room and must fight his way through the dungeon to rescue the princess.

The knight has an initial health point represented by a positive integer. If at any point his health point drops to 0 or below, he dies immediately.

Some of the rooms are guarded by demons, so the knight loses health (negative integers) upon entering these rooms; other rooms are either empty (0's) or contain magic orbs that increase the knight's health (positive integers).

In order to reach the princess as quickly as possible, the knight decides to move only rightward or downward in each step.

Write a function to determine the knight's minimum initial health so that he is able to rescue the princess.

#####Note:
- The knight's health has no upper bound.
- Any room can contain threats or power-ups, even the first room the knight enters and the bottom-right room where the princess is imprisoned.

### 解题思路

动态规划，dp[i][j]表示到(i, j)这个格的时候，最少需要多少血量，dp[0][0]为所求
```
dp[m][n] = max(1, 1 - dungeon[-1][-1])
dp[m][j] = max(1, dp[m][j + 1] - dungeon[m][j])
dp[i][n] = max(1, dp[i + 1][n] - dungeon[i][n])
dp[i][j] = max(1, min(dp[i][j + 1], dp[i + 1][j]) - dungeon[i][j])
```

### 代码
```python
class Solution:
    def calculateMinimumHP(self, dungeon: List[List[int]]) -> int:
        m, n = len(dungeon), len(dungeon[0])
        dp = [0] * n
        dp[-1] = max(1, 1 - dungeon[-1][-1])
        for j in range(n - 2, -1, -1):
            dp[j] = max(1, dp[j + 1] - dungeon[-1][j])
        for i in range(m - 2, -1, -1):
            dp[-1] = max(1, dp[-1] - dungeon[i][-1])
            for j in range(n - 2, -1, -1):
                dp[j] = max(1, min(dp[j], dp[j + 1]) - dungeon[i][j])
        return dp[0]
```
