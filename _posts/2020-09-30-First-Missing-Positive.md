---
layout:     post
title:      LeetCode 41 First Missing Positive (Python)
number:     41
level:      Hard
lcurl:      first-missing-positive
youtube:    p0wrWTCABK8
bilibili1:  //player.bilibili.com/player.html?aid=797293406&bvid=BV1fy4y1k7pV&cid=240488339&page=1
xigua:      
date:       2020-09-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an unsorted integer array, find the smallest missing positive integer.

### 解题思路

如果数组的长度是l，那么结果最大就是l+1，所以吧所有负数和大于l+1的数，都变成0，给数组加一个0（处理0的情况），然后遍历数组，把数对应下标的数加上l+1，最后再遍历一遍，第一个小于等于l的数，就是结果

### 代码
```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        nums.append(0)
        l = len(nums)
        if l == 1:
            return 1
        for i in range(l):
            if nums[i] < 0 or nums[i] >= l:
                nums[i] = 0
        for i in range(l):
            nums[nums[i] % l] += l
        for i in range(1, l):
            if nums[i] < l:
                return i
        return l
```
