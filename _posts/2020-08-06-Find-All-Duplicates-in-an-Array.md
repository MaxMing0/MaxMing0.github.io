---
layout:     post
title:      LeetCode 442 Find All Duplicates in an Array (Python)
number:     442
level:      Medium
lcurl:      find-all-duplicates-in-an-array
youtube:    Jgz2nHjydUY
bilibili1:  //player.bilibili.com/player.html?aid=201631632&bvid=BV1Lh411d7AD&cid=221125396&page=1
xigua:      
date:       2020-08-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements that appear twice in this array.

Could you do it without extra space and in O(n) runtime?

### 解题思路

因为每个数的大小小于等于数组长度，可以用数对应下标的数的正负号进行标记，把遇到的数对应的数变成负，如果已经是负数了，则证明已经出现过

### 代码
```python
class Solution:
    def findDuplicates(self, nums: List[int]) -> List[int]:
        res = []
        for i in range(len(nums)):
            ind = abs(nums[i]) - 1
            if nums[ind] < 0:
                res.append(ind + 1)
            else:
                nums[ind] *= -1
        return res
```
