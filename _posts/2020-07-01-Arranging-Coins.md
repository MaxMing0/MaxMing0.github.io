---
layout:     post
title:      LeetCode 441 Arranging Coins (Python)
number:     441
level:      Easy
lcurl:      arranging-coins
youtube:    nwkL26xlYI0
bilibili1:  //player.bilibili.com/player.html?aid=413655341&bvid=BV1eV411k7rg&cid=207729863&page=1
xigua:      
date:       2020-07-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.

### 解题思路
```
1 + 2 + ... + k <= N
先转换成等式
k = (-1+sqrt(1+8*n))/2
最后的答案是k的取整
```
### 代码
```python
class Solution:
    def arrangeCoins(self, n: int) -> int:
        return int((-1 + math.sqrt(1 + 8 * n)) / 2)
```
