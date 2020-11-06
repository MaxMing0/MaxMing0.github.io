---
layout:     post
title:      LeetCode 1283 Find the Smallest Divisor Given a Threshold (Python)
number:     1283
level:      Medium
lcurl:      find-the-smallest-divisor-given-a-threshold
youtube:    7UhuS3mfae0
bilibili1:  //player.bilibili.com/player.html?aid=245194847&bvid=BV1Fv411r7Nw&cid=253122125&page=1
xigua:      
date:       2020-11-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

二分答案，左右边界为1和最大的数，注意这个除法是上取整

### 解题思路

Given an array of integers nums and an integer threshold, we will choose a positive integer divisor and divide all the array by it and sum the result of the division. Find the smallest divisor such that the result mentioned above is less than or equal to threshold.

Each result of division is rounded to the nearest integer greater than or equal to that element. (For example: 7/3 = 3 and 10/2 = 5).

It is guaranteed that there will be an answer.

### 代码
```python
class Solution:
    def smallestDivisor(self, nums: List[int], threshold: int) -> int:
        l, r = 1, max(nums)
        res = 0
        while l <= r:
            m = (l + r) // 2
            tot = sum((x - 1) // m + 1 for x in nums)
            if tot <= threshold:
                res = m
                r = m - 1
            else:
                l = m + 1
        return res
```
