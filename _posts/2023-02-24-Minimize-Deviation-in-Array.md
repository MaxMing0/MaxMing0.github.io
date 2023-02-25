---
layout:     post
title:      LeetCode 1675 Minimize Deviation in Array (Python)
number:     1675
level:      Hard
lcurl:      minimize-deviation-in-array
youtube:    yPVbGhC3yDo
bilibili1:  
xigua:      
date:       2023-02-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given an array nums of n positive integers.

You can perform two types of operations on any element of the array any number of times:

If the element is even, divide it by 2.
For example, if the array is [1,2,3,4], then you can do this operation on the last element, and the array will be [1,2,3,2].
If the element is odd, multiply it by 2.
For example, if the array is [1,2,3,4], then you can do this operation on the first element, and the array will be [2,2,3,4].
The deviation of the array is the maximum difference between any two elements in the array.

Return the minimum deviation the array can have after performing some number of operations.

### 解题思路

贪心，先把所有奇数 * 2，然后每次都取最大的数，和最小的数做差，更新结果，直到最大的数是奇数，结束循环

### 代码
```python
class Solution:
    def minimumDeviation(self, nums: List[int]) -> int:
        q = []
        for n in nums:
            q.append(-2 * n if n & 1 else -n)
        res, maxv = float('inf'), max(q)
        heapq.heapify(q)
        while True:
            t = heapq.heappop(q)
            res = min(res, maxv - t)
            if t & 1:
                break
            t >>= 1
            maxv = max(maxv, t)
            heapq.heappush(q, t)
        return res
```
