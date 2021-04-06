---
layout:     post
title:      LeetCode 1551 Minimum Operations to Make Array Equal (Python)
number:     1551
level:      Medium
lcurl:      minimum-operations-to-make-array-equal
youtube:    iqLPxV29W0A
bilibili1:  //player.bilibili.com/player.html?aid=757458764&bvid=BV1u64y1S7fx&cid=320579549&page=1
xigua:      
date:       2021-04-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

You have an array arr of length n where arr[i] = (2 * i) + 1 for all valid values of i (i.e. 0 <= i < n).

In one operation, you can select two indices x and y where 0 <= x, y < n and subtract 1 from arr[x] and add 1 to arr[y] (i.e. perform arr[x] -=1 and arr[y] += 1). The goal is to make all the elements of the array equal. It is guaranteed that all the elements of the array can be made equal using some operations.

Given an integer n, the length of the array. Return the minimum number of operations needed to make all the elements of arr equal.

### 解题思路
```
奇数 n*((n-1)/2) - (1+(n-2))*(n-1)/2/2 = (n*n-1)/4
偶数 n*(n/2) - (1+(n-1))*(n/2)/2 = n*n/4
```
### 代码
```python
class Solution:
    def minOperations(self, n: int) -> int:
        return n * n // 4
```
