---
layout:     post
title:      LeetCode 954 Array of Doubled Pairs (Python)
number:     954
level:      Medium
lcurl:      array-of-doubled-pairs
youtube:    lIcK9d9p_gM
bilibili1:  //player.bilibili.com/player.html?aid=589854248&bvid=BV1Hq4y1S7xR&cid=387320018&page=1
xigua:      
date:       2021-08-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Given an integer array of even length arr, return true if it is possible to reorder arr such that arr[2 * i + 1] = 2 * arr[2 * i] for every 0 <= i < len(arr) / 2, or false otherwise.

### 解题思路

贪心，使用计数器求出每个数出现的次数，然后按绝对值从小到大，如果当前数为n，查看2n出现的次数是否大于等于n

### 代码
```python
class Solution:
    def canReorderDoubled(self, arr: List[int]) -> bool:
        ct = collections.Counter(arr)
        for n in sorted(ct, key=abs):
            if ct[n] > ct[2 * n]:
                return False
            ct[2 * n] -= ct[n]
        return True
```
