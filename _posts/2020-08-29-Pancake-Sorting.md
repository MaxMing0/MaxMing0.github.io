---
layout:     post
title:      LeetCode 969 Pancake Sorting (Python)
number:     969
level:      Medium
lcurl:      pancake-sorting
youtube:    J3ftj2Hxvv0
bilibili1:  //player.bilibili.com/player.html?aid=754410714&bvid=BV1hk4y127yJ&cid=230212796&page=1
xigua:      
date:       2020-08-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

Given an array of integers A, We need to sort the array performing a series of pancake flips.

In one pancake flip we do the following steps:
- Choose an integer k where 0 <= k < A.length.
- Reverse the sub-array A[0...k].
For example, if A = [3,2,1,4] and we performed a pancake flip choosing k = 2, we reverse the sub-array [3,2,1], so A = [1,2,3,4] after the pancake flip at k = 2.

Return an array of the k-values of the pancake flips that should be performed in order to sort A. Any valid answer that sorts the array within 10 * A.length flips will be judged as correct.

### 解题思路

每次找最大的煎饼，先翻到第一个位置，再翻到最后一个位置，经过2n次，可以得到结果

### 代码
```python
class Solution:
    def pancakeSort(self, A: List[int]) -> List[int]:
        result, n = [], len(A)
        for i in range(n, 0, -1):
            pos = A.index(i)
            if pos == i - 1:
                continue
            if pos != 0:
                result.append(pos + 1)
                A[: pos + 1] = A[: pos + 1][::-1]
            result.append(i)
            A[:i] = A[:i][::-1]
        return result
```
