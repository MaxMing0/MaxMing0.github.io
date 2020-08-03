---
layout:     post
title:      LeetCode 1534 Count Good Triplets (Python)
number:     1534
level:      Easy
lcurl:      count-good-triplets
youtube:    dvLi35uwiQo
bilibili1:  //player.bilibili.com/player.html?aid=754095542&bvid=BV11k4y1m7rV&cid=219757980&page=1
xigua:      
date:       2020-08-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an array of integers arr, and three integers a, b and c. You need to find the number of good triplets.

A triplet (arr[i], arr[j], arr[k]) is good if the following conditions are true:

- 0 <= i < j < k < arr.length
- |arr[i] - arr[j]| <= a
- |arr[j] - arr[k]| <= b
- |arr[i] - arr[k]| <= c
Where |x| denotes the absolute value of x.

Return the number of good triplets.

### 解题思路

遍历ijk，判断是否符合条件

### 代码
```python
class Solution:
    def countGoodTriplets(self, arr: List[int], a: int, b: int, c: int) -> int:
        res = 0
        n = len(arr)
        for i in range(n - 2):
            for j in range(i + 1, n - 1):
                if math.fabs(arr[j] - arr[i]) > a:
                    continue
                for k in range(j + 1, n):
                    if math.fabs(arr[k]-arr[i]) <= c or math.fabs(arr[k] - arr[j]) <= b:
                        res += 1
        return res
```
