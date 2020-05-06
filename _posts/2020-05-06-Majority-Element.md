---
layout:     post
title:      LeetCode 169 Majority Element (Python)
number:     169
level:      Easy
lcurl:      majority-element
youtube:    MGJkXgQri8k
bilibili1:  //player.bilibili.com/player.html?aid=285610133&bvid=BV1Ff4y1U7Vn&cid=187737505&page=1
xigua:      
date:       2020-05-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

### 解题思路

将数组转换成计数器，遍历计数器中的每一项，找出现次数大于`n/2`的数

### 代码
```python
from collections import Counter
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        ct = Counter(nums)
        l = len(nums) / 2
        for key, value in ct.items():
            if value >= l:
                return key
```
