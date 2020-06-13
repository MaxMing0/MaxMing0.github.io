---
layout:     post
title:      LeetCode 368 Largest Divisible Subset (Python)
number:     368
level:      Medium
lcurl:      largest-divisible-subset
youtube:    https://youtu.be/YzCbp19FugM
bilibili1:  //player.bilibili.com/player.html?aid=711119331&bvid=BV15D4y1Q74b&cid=201611373&page=1
xigua:      
date:       2020-06-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a set of distinct positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies:

Si % Sj = 0 or Sj % Si = 0.

If there are multiple solutions, return any subset is fine.

### 解题思路

(A1, A2, ... An) -> DS, A1 < A2 < ... < An, x % An == 0 => (A1, A2, ... An, x) -> DS

DP, 先对所有数排序，dp[i]表示以第i个数为集合中最大元素的divisible subset，最多的元素个数，在更新的时候需要记录路径
```
dp[0] = 1
dp[i] = max(dp[k]) + 1, if nums[i] % nums[k] = 0, 0 <= k < i
```

### 代码
```python
class Solution:
    def largestDivisibleSubset(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
        nums.sort()
        dp = [[0, i] for i in range(len(nums))]
        idx = max_len = 0
        for i, num in enumerate(nums):
            tmp = 0
            for k in range(i):
                if nums[i] % nums[k] == 0:
                    if tmp < dp[k][0]:
                        tmp = dp[k][0]
                        dp[i][1] = k
            dp[i][0] = tmp + 1
            if dp[i][0] > max_len:
                max_len = dp[i][0]
                idx = i

        res = [nums[idx]]
        while idx != dp[idx][1]:
            idx = dp[idx][1]
            res.append(nums[idx])
        return res[::-1]
```
