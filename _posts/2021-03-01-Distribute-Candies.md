---
layout:     post
title:      LeetCode 575 Distribute Candies (Python)
number:     575
level:      Easy
lcurl:      distribute-candies
youtube:    M6GZulTB3p0
bilibili1:  //player.bilibili.com/player.html?aid=544401971&bvid=BV11i4y1T7Pr&cid=305080086&page=1
xigua:      
date:       2021-03-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Alice has n candies, where the ith candy is of type candyType[i]. Alice noticed that she started to gain weight, so she visited a doctor.

The doctor advised Alice to only eat n / 2 of the candies she has (n is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice.

Given the integer array candyType of length n, return the maximum number of different types of candies she can eat if she only eats n / 2 of them.

### 解题思路

如果种类小于n答案为种类的个数，否则为n/2

### 代码
```python
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        return min(len(candyType) // 2, len(set(candyType)))
```
