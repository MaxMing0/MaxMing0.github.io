---
layout:     post
title:      LeetCode 260 Single Number III (Python)
number:     260
level:      Medium
lcurl:      single-number-iii
youtube:    HL0yhe8Aoi0
bilibili1:  //player.bilibili.com/player.html?aid=498997626&bvid=BV1QK411J7dN&cid=215705631&page=1
xigua:      
date:       2020-07-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

### 解题思路

先把所有数异或，结果为1的位置则是这两数的差异，选取最后一个位1的位置，将所有数按照这个位置的不同分成两组，将每组再次异或就是结果

### 代码
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> List[int]:
        bitmask = 0
        for n in nums:
            bitmask ^= n
        diff = bitmask & (-bitmask)
        x = 0
        for n in nums:
            if n & diff:
                x ^= n
        return [x, x ^ bitmask]
```
