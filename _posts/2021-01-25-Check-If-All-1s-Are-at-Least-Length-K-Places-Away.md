---
layout:     post
title:      LeetCode 1437 Check If All 1's Are at Least Length K Places Away (Python)
number:     1437
level:      Easy
lcurl:      check-if-all-1s-are-at-least-length-k-places-away
youtube:    4-O2yyxpyGw
bilibili1:  //player.bilibili.com/player.html?aid=373869557&bvid=BV1Yo4y1R78P&cid=287718363&page=1
xigua:      
date:       2021-01-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array nums of 0s and 1s and an integer k, return True if all 1's are at least k places away from each other, otherwise return False.

### 解题思路

遍历数组，遇到1计算距上一个1出现的距离

### 代码
```python
class Solution:
    def kLengthApart(self, nums: List[int], k: int) -> bool:
        ct = k
        for n in nums:
            if n:
                if ct < k:
                    return False
                ct = 0
            else:
                ct += 1
        return True
```
