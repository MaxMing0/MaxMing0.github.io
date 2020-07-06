---
layout:     post
title:      LeetCode 1502 Can Make Arithmetic Progression From Sequence (Python)
number:     1502
level:      Easy
lcurl:      can-make-arithmetic-progression-from-sequence
youtube:    KTDg3MPjcQ8
bilibili1:  //player.bilibili.com/player.html?aid=926277236&bvid=BV12T4y177vU&cid=209364624&page=1
xigua:      
date:       2020-07-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an array of numbers arr. A sequence of numbers is called an arithmetic progression if the difference between any two consecutive elements is the same.

Return true if the array can be rearranged to form an arithmetic progression, otherwise, return false.

### 解题思路

1. 先排序，判断相邻两个数之差是否相同
2. 求出等差数列首项，末项和公差，对所有数减去首项，判断是否都为公差的倍数，且所有数不同，或公差为0

### 代码
```python
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        arr.sort()
        d = arr[1] - arr[0]
        for i in range(2, len(arr)):
            if arr[i] - arr[i - 1] != d:
                return False
        return True
```
```python
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        A1, An, n = min(arr), max(arr), len(arr)
        d = (An - A1) / (n - 1)
        if d == 0: return True
        s = set(a - A1 for a in arr)
        return len(s) == n and all(a % d == 0 for a in s)
```
