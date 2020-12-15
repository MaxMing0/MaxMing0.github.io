---
layout:     post
title:      LeetCode 977 Squares of a Sorted Array (Python)
number:     977
level:      Easy
lcurl:      squares-of-a-sorted-array
youtube:    ePaOzjK7p_8
bilibili1:  //player.bilibili.com/player.html?aid=713186231&bvid=BV1EX4y1u7Mb&cid=266982200&page=1
xigua:      
date:       2020-12-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

### 解题思路

使用双指针，从两端开始，每次将绝对值较大的数的平方倒序加到结果里

### 代码
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l = len(nums)
        left, right = 0, l - 1
        res = [0] * l
        cur = l - 1
        while left <= right:
            if abs(nums[left]) > abs(nums[right]):
                res[cur] = nums[left] ** 2
                left += 1
            else:
                res[cur] = nums[right] ** 2
                right -= 1
            cur -= 1
        return res
```
