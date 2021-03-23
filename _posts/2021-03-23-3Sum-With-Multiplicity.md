---
layout:     post
title:      LeetCode 923 3Sum With Multiplicity (Python)
number:     923
level:      Medium
lcurl:      3sum-with-multiplicity
youtube:    VHkgA1y0Iiw
bilibili1:  //player.bilibili.com/player.html?aid=247261463&bvid=BV1Pv41187sq&cid=314220832&page=1
xigua:      
date:       2021-03-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
    - Two Pointers
---

### 题目

Given an integer array arr, and an integer target, return the number of tuples i, j, k such that i < j < k and arr[i] + arr[j] + arr[k] == target.

As the answer can be very large, return it modulo 10^9 + 7.

### 解题思路

1. 统计每个数出现的次数，枚举两个数判断第三个数是否出现在计数器中，并且要求三个数的顺序，通过组合数求所有的可能数
2. 先排序，枚举第一个数，剩余的数相当于做一个Two Sum

### 代码
```python
class Solution:
    def threeSumMulti(self, arr: List[int], target: int) -> int:
        res = 0
        MOD = 10**9 + 7
        ct = Counter(arr)
        for x in ct:
            for y in ct:
                if x > y:
                    continue
                z = target - x - y
                if y <= z and z in ct:
                    if x == y == z:
                        res += ct[x] * (ct[x] - 1) * (ct[x] - 2) // 6
                    elif x == y:
                        res += ct[x] * (ct[x] - 1) * ct[z] // 2
                    elif x == z:
                        res += ct[x] * (ct[x] - 1) * ct[y] // 2
                    elif y == z:
                        res += ct[x] * ct[y] * (ct[y] - 1) // 2
                    else:
                        res += ct[x] * ct[y] * ct[z]
        return res % MOD
```
