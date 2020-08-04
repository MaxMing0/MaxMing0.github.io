---
layout:     post
title:      LeetCode 1535 Find the Winner of an Array Game (Python)
number:     1535
level:      Medium
lcurl:      find-the-winner-of-an-array-game
youtube:    hRnSn_06evA
bilibili1:  //player.bilibili.com/player.html?aid=969003218&bvid=BV1Xp4y1i7ey&cid=220267675&page=1
xigua:      
date:       2020-08-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an integer array arr of distinct integers and an integer k.

A game will be played between the first two elements of the array (i.e. arr[0] and arr[1]). In each round of the game, we compare arr[0] with arr[1], the larger integer wins and remains at position 0 and the smaller integer moves to the end of the array. The game ends when an integer wins k consecutive rounds.

Return the integer which will win the game.

It is guaranteed that there will be a winner of the game.

### 解题思路

当`k>=n-1`时，答案就是最大的数，如果不是，就按照题目要求进行比较，但是只需要维护一个指针指向当前赢的数，以及赢的次数，当赢了k次之后，返回这个数，如果当遍历完所有数依旧没有赢k次，最后答案依旧是最大的数

### 代码
```python
class Solution:
    def getWinner(self, arr: List[int], k: int) -> int:
        n = len(arr)
        if k >= n - 1:
            return max(arr)
        cur = arr[0]
        win = 0
        for i in range(1, n):
            if arr[i] > cur:
                cur = arr[i]
                win = 0
            win += 1
            if win == k:
                break
        return cur
```
