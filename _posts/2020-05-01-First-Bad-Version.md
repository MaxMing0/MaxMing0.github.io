---
layout:     post
title:      LeetCode 278 First Bad Version (Python)
number:     278
level:      East
lcurl:      first-bad-version
youtube:    mKRS6H0tDqo
bilibili1:  //player.bilibili.com/player.html?aid=710467698&bvid=BV1cQ4y1N7dc&cid=185573559&page=1
xigua:      
date:       2020-05-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

### 解题思路

这道题就是一个标准的二分，找到第一个坏版本号出现的位置

### 代码
```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):

class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        l, r = 1, n
        while l < r:
            m = (l + r) // 2
            if isBadVersion(m):
                r = m
            else:
                l = m + 1
        return l
```
