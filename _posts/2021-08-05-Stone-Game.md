---
layout:     post
title:      LeetCode 877 Stone Game (Python)
number:     877
level:      Medium
lcurl:      stone-game
youtube:    pDliU9K5E6w
bilibili1:  //player.bilibili.com/player.html?aid=589704406&bvid=BV1xq4y1Q7uL&cid=383402060&page=1
xigua:      
date:       2021-08-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Alex and Lee play a game with piles of stones.  There are an even number of piles arranged in a row, and each pile has a positive integer number of stones piles[i].

The objective of the game is to end with the most stones.  The total number of stones is odd, so there are no ties.

Alex and Lee take turns, with Alex starting first.  Each turn, a player takes the entire pile of stones from either the beginning or the end of the row.  This continues until there are no more piles left, at which point the person with the most stones wins.

Assuming Alex and Lee play optimally, return True if and only if Alex wins the game.

### 解题思路

先拿的人一定可以选择拿完全部的奇数堆或者偶数堆，选这两个较大的拿

### 代码
```python
class Solution:
    def stoneGame(self, piles: List[int]) -> bool:
        return True
```
