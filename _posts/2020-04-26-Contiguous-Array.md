---
layout:     post
title:      LeetCode 525 Contiguous Array (Python)
number:     525
level:      Medium
lcurl:      contiguous-array
youtube:    -T0-xmdKw-w
bilibili1:  //player.bilibili.com/player.html?aid=455227784&bvid=BV185411t7tu&cid=177808591&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

### 解题思路



### 代码
```python
class Solution:
    def findMaxLength(self, nums: List[int]) -> int:
        res = ct = 0
        dic = {0: 0}
        for i, n in enumerate(nums, 1):
            ct += 1 if n else -1
            if ct in dic:
                res = max(res, i - dic[ct])
            else:
                dic[ct] = i
        return res
```