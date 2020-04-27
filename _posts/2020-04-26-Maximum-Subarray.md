---
layout:     post
title:      LeetCode 53 Maximum Subarray (Python)
number:     53
level:      Easy
lcurl:      happy-number
youtube:    9RCR1vyJq5A
bilibili1:  //player.bilibili.com/player.html?aid=327546128&bvid=BV11A41187AR&cid=173439380&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
    - Math
---

### 题目
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

### 解题思路



### 代码
```python
class Solution:
    def isHappy(self, n: int) -> bool:
        s = {n}
        while n != 1:
            tmp = sum([int(c) ** 2 for c in str(n)])
            if tmp in s:
                return False
            s.add(tmp)
            n = tmp
        return True
```