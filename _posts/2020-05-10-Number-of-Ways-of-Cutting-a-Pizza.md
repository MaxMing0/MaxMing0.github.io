---
layout:     post
title:      LeetCode 1444 Number of Ways of Cutting a Pizza (Python)
number:     1444
level:      Hard
lcurl:      number-of-ways-of-cutting-a-pizza
youtube:    aLjKRZS33As
bilibili1:  //player.bilibili.com/player.html?aid=838145319&bvid=BV1gg4y1B7zS&cid=189659261&page=1
xigua:      
date:       2020-05-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a rectangular pizza represented as a rows x cols matrix containing the following characters: 'A' (an apple) and '.' (empty cell) and given the integer k. You have to cut the pizza into k pieces using k-1 cuts. 

For each cut you choose the direction: vertical or horizontal, then you choose a cut position at the cell boundary and cut the pizza into two pieces. If you cut the pizza vertically, give the left part of the pizza to a person. If you cut the pizza horizontally, give the upper part of the pizza to a person. Give the last piece of pizza to the last person.

Return the number of ways of cutting the pizza such that each piece contains at least one apple. Since the answer can be a huge number, return this modulo 10^9 + 7.

### 解题思路

DP, dp[k][i][j]表示还是当前剩下的pizza是从（i,j）到（row,col）还需要切k刀的分法，dp[k-1][0][0]为最后的结果

初始值，如果从(i,j)到(row,col)有苹果 dp[0][i][j] = 1，否则是0

转移方程
```latex
dp(k, i, j) = check(i, j, row, col) if k == 0
            = \sum_{t=i+1}^{row} dp(k - 1, t, j) if check(i, j, t, col) 
            + \sum_{t=j+1}^{col} dp(k - 1, i, t) if check(i, j, row, t)
```

判断（x1,y1）到（x2,y2）有没有苹果的方法是使用二维的部分和数组，ps[i][j]表示从(0,0)到(i,j)的苹果的个数，

如果`ps[x2][y2] - ps[x1][y2] - ps[x2][y1] + ps[x1][y1] > 0`，那么这块pizza上就有苹果

### 代码
```python
class Solution:
    def ways(self, pizza: List[str], k: int) -> int:
        def check(x1, y1, x2, y2):
            return ps[x2][y2] - ps[x1][y2] - ps[x2][y1] + ps[x1][y1] > 0

        def mem(k, i, j):
            tmp = 0
            for t in range(i + 1, row + 1):
                if check(i, j, t, col):
                    if dp[k - 1][t][j] == -1:
                        mem(k - 1, t, j)
                    tmp += dp[k-1][t][j]
            for t in range(j + 1, col + 1):
                if check(i, j, row, t):
                    if dp[k - 1][i][t] == -1:
                        mem(k - 1, i, t)
                    tmp += dp[k - 1][i][t]
            tmp = tmp % 1000000007
            dp[k][i][j] = tmp
            return tmp
        
        row, col = len(pizza), len(pizza[0])
        ps = [[0] * (col + 1) for _ in range(row + 1)]
        for i in range(1, row + 1):
            for j in range(1, col + 1):
                ps[i][j] = ps[i - 1][j] + ps[i][j - 1] - ps[i - 1][j - 1] + int(pizza[i - 1][j - 1] == 'A')
        if k == 1:
            return int(check(0,0,row,col))
        dp = [[[-1] * (col + 1) for i in range(row + 1)] for j in range(k)]
        for i in range(row + 1):
            for j in range(col + 1):
                dp[0][i][j] = int(check(i, j, row, col))
        return mem(k-1, 0, 0)
```
