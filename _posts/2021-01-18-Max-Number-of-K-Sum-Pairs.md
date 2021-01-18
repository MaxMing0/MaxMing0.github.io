---
layout:     post
title:      LeetCode 1679 Max Number of K-Sum Pairs (Python)
number:     1679
level:      Medium
lcurl:      max-number-of-k-sum-pairs
youtube:    PvB-yz_yOW4
bilibili1:  //player.bilibili.com/player.html?aid=628687677&bvid=BV16t4y1z7kY&cid=284097242&page=1
xigua:      
date:       2021-01-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

You are given an integer array nums and an integer k.

In one operation, you can pick two numbers from the array whose sum equals k and remove them from the array.

Return the maximum number of operations you can perform on the array.

### 解题思路

使用一个计数器求出每个数出现的次数，遍历计数器，找到当前数字与其对应数字出现的较少次数，单独处理`k/2`的情况

### 代码
```python
class Solution:
    def maxOperations(self, nums: List[int], k: int) -> int:
        ct = Counter(nums)
        res = 0
        for n in ct:
            tmp = k - n
            if n == tmp:
                res += ct[n] // 2
                continue    
            if n < tmp:
                res += min(ct[n], ct[tmp])
        return res
```
