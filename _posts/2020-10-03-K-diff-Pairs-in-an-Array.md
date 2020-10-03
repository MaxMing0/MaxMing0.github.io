---
layout:     post
title:      LeetCode 532 K-diff Pairs in an Array (Python)
number:     532
level:      Medium
lcurl:      k-diff-pairs-in-an-array
youtube:    //player.bilibili.com/player.html?aid=414850369&bvid=BV1MV41127o1&cid=241653663&page=1
bilibili1:  
xigua:      
date:       2020-10-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.

A k-diff pair is an integer pair (nums[i], nums[j]), where the following are true:

- 0 <= i, j < nums.length
- i != j
- a <= b
- b - a == k

### 解题思路

使用计数器统计每个数出现次数，如果k=0，那么结果是有多少个数出现过2次以上，否则，遍历每个数n，判断n+k是否出现过

### 代码
```python
class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        ct = Counter(nums)
        res = 0
        if k == 0:
            for v in ct.values():
                res += v > 1
        else:
            for n in ct:
                res += k + n in ct
        return res
```
