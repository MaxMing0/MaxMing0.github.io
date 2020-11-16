---
layout:     post
title:      LeetCode 845 Longest Mountain in Array (Python)
number:     845
level:      Medium
lcurl:      longest-mountain-in-array
youtube:    2cUhalOGJB8
bilibili1:  //player.bilibili.com/player.html?aid=542801616&bvid=BV1zi4y1L7yV&cid=256469594&page=1
xigua:      
date:       2020-11-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Let's call any (contiguous) subarray B (of A) a mountain if the following properties hold:

- B.length >= 3
- There exists some 0 < i < B.length - 1 such that B[0] < B[1] < ... B[i-1] < B[i] > B[i+1] > ... > B[B.length - 1]
(Note that B could be any subarray of A, including the entire array A.)

Given an array A of integers, return the length of the longest mountain. 

Return 0 if there is no mountain.

### 解题思路

两个指针，确定左山脚，向右寻找右山脚

### 代码
```python
class Solution:
    def longestMountain(self, A: List[int]) -> int:
        n = len(A)
        res = l = 0
        while l + 2 < n:
            r = l + 1
            if A[l] < A[l + 1]:
                while r + 1 < n and A[r] < A[r + 1]:
                    r += 1
                if r < n - 1 and A[r] > A[r + 1]:
                    while r + 1 < n and A[r] > A[r + 1]:
                        r += 1
                    res = max(res, r - l + 1)
                else:
                    r += 1
            l = r
        return res
```
