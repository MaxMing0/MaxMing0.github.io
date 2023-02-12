---
layout:     post
title:      LeetCode 1470 Shuffle the Array (Python)
number:     1470
level:      Easy
lcurl:      shuffle-the-array
youtube:    t-Ubgcy1jzw
bilibili1:  
xigua:      
date:       2023-02-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
    - Bit Manipulation
---

### 题目

Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].

### 解题思路

创建一个新数组，按照要求写入x1,y1,x2,y2...xnyn

使用位运算，先把y1...yn放到x1...xn的高位，再从后向前遍历，把每个数分成两个数，写到对应位置

### 代码
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        res = []
        for i in range(n):
            res.append(nums[i])
            res.append(nums[i + n])
        return res
```
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        for i in range(n):
            nums[i] |= nums[i + n] << 10
        ones = int(pow(2, 10)) - 1
        for i in range(n - 1, -1, -1):
            xi = nums[i] & ones
            yi = nums[i] >> 10
            nums[2 * i + 1] = yi
            nums[2 * i] = xi
        return nums
```
