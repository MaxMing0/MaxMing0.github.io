---
layout:     post
title:      LeetCode 910 Smallest Range II (Python)
number:     910
level:      Medium
lcurl:      smallest-range-ii
youtube:    7HPrdUHO_Kg
bilibili1:  //player.bilibili.com/player.html?aid=458230791&bvid=BV1p5411H7mS&cid=269303836&page=1
xigua:      
date:       2020-12-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Given an array A of integers, for each integer A[i] we need to choose either x = -K or x = K, and add x to A[i] (only once).

After this process, we have some array B.

Return the smallest possible difference between the maximum value of B and the minimum value of B.

### 解题思路

贪心，先排序，枚举每个位置，对所有左边的数+k，右边的数-k，求出最大的差值，取最小的为结果

### 代码
```python
class Solution:
    def smallestRangeII(self, A: List[int], K: int) -> int:
        A = sorted(set(A))
        lo, hi = A[0], A[-1]
        res = hi - lo
        if res <= K:
            return res
        if res >= 4 * K:
            return res - K * 2
        for i in range(len(A) - 1):
            a, b = A[i], A[i + 1]
            res = min(res, max(hi - K, a + K) - min(lo + K, b - K))
        return res
```
