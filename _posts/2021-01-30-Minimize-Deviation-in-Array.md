---
layout:     post
title:      LeetCode 1675 Minimize Deviation in Array (Python)
number:     1675
level:      Hard
lcurl:      minimize-deviation-in-array
youtube:    mKGGMdMwpGE
bilibili1:  //player.bilibili.com/player.html?aid=288933404&bvid=BV16f4y167uf&cid=290387494&page=1
xigua:      
date:       2021-01-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an array nums of n positive integers.

You can perform two types of operations on any element of the array any number of times:

- If the element is even, divide it by 2.
  - For example, if the array is [1,2,3,4], then you can do this operation on the last element, and the array will be [1,2,3,2].
- If the element is odd, multiply it by 2.
  - For example, if the array is [1,2,3,4], then you can do this operation on the first element, and the array will be [2,2,3,4].
The deviation of the array is the maximum difference between any two elements in the array.

Return the minimum deviation the array can have after performing some number of operations.

### 解题思路

将奇数*2，和所有偶数一起放入优先队列，每次pop出最大的，和最小的做差更新结果，最大的是奇数时结束循环

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
