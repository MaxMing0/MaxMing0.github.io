---
layout:     post
title:      LeetCode 605 Can Place Flowers (Python)
number:     605
level:      Easy
lcurl:      can-place-flowers
youtube:    pqLhqhm5cnQ
bilibili1:  //player.bilibili.com/player.html?aid=585523014&bvid=BV1Uz4y1k7xU&cid=263176664&page=1
xigua:      
date:       2020-12-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule.

### 解题思路

贪心，从左向右遍历，如果能种花，就种，最后查看最多能种多少花，要处理两端的情况

### 代码
```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        count = 0
        flowerbed.extend([0, 0])
        for i in range(len(flowerbed) - 2):
            if flowerbed[i - 1] == flowerbed[i] == flowerbed[i + 1] == 0:
                flowerbed[i] = 1
                count += 1
        return count >= n
```
