---
layout:     post
title:      LeetCode 941 Valid Mountain Array (Python)
number:     941
level:      Medium
lcurl:      valid-mountain-array
youtube:    wf0mLPAoddw
bilibili1:  //player.bilibili.com/player.html?aid=458036235&bvid=BV1n5411G7qs&cid=265000864&page=1
xigua:      
date:       2020-12-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of integers arr, return true if and only if it is a valid mountain array.

Recall that arr is a mountain array if and only if:

- arr.length >= 3
- There exists some i with 0 < i < arr.length - 1 such that:
  - arr[0] < arr[1] < ... < arr[i - 1] < A[i]
  - arr[i] > arr[i + 1] > ... > arr[arr.length - 1]

### 解题思路

使用两个指针从两次分别上山，判断两个指针能否相遇，且相遇的位置不是在两端

### 代码
```python
class Solution:
    def validMountainArray(self, arr: List[int]) -> bool:
        if len(arr) < 3:
            return False
        i, j = 0, len(arr) - 1
        while i < len(arr) - 1 and arr[i] < arr[i + 1]:
            i += 1
        while j >= 0 and arr[j] < arr[j - 1]:
            j -= 1
        return i == j and i != 0 and j != len(arr) - 1
```
