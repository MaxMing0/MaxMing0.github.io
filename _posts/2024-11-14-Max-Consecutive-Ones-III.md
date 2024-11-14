---
layout:     post
title:      LeetCode 1004 Max Consecutive Ones III (Python)
number:     1004
level:      Medium
lcurl:      max-consecutive-ones-iii
youtube:    
bilibili1:  
xigua:      
date:       2024-11-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.

### 解题思路

两个指针，如果右指针是0，k-1，当k<0的时候，同时移动指针，如果做指针是0，k+1，由于不会缩短窗口的长度，无需记录最大值

### 代码
```python
class Solution:
    def longestOnes(self, nums: List[int], k: int) -> int:
        i = 0
        for j in range(len(nums)):
            k -= 1 - nums[j]
            if k < 0:
                k += 1 - nums[i]
                i += 1
        return j - i + 1
```
