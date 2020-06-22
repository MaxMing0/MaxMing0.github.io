---
layout:     post
title:      LeetCode 137 Single Number II (Python)
number:     137
level:      Medium
lcurl:      single-number-ii
youtube:    EAEkP7LOJmQ
bilibili1:  //player.bilibili.com/player.html?aid=243603193&bvid=BV1Hv411B7rd&cid=204610680&page=1
xigua:      
date:       2020-06-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a non-empty array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

### 解题思路

位运算做法请参考[博客](https://blog.csdn.net/yutianzuijin/article/details/50597413)

### 代码
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return (3 * sum(set(nums)) - sum(nums)) // 2
```
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        res = 0
        for i in range(32):
            ct = 0
            for n in nums:
                ct += (n >> i) & 1
            res |= (ct % 3) << i
        return res - 2**32 if res >> 31 & 1 else res
```
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        low = high = 0;
        for n in nums:
            low = (low ^ n) & ~high;
            high = (high ^ n) & ~low;
        return low
```
