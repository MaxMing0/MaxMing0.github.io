---
layout:     post
title:      LeetCode 220 Contains Duplicate III (Python)
number:     220
level:      Medium
lcurl:      contains-duplicate-iii
youtube:    CMaH086nKl4
bilibili1:  //player.bilibili.com/player.html?aid=201894043&bvid=BV19h41197iw&cid=231535597&page=1
xigua:      
date:       2020-09-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

Given an array of integers, find out whether there are two distinct indices i and j in the array such that the absolute difference between nums[i] and nums[j] is at most t and the absolute difference between i and j is at most k.

### 解题思路

1. 直接按照题目要求遍历
2. 维护一个大小为k的平衡树，对于每个新来的数，找到第一个比它大和比它小的数，判断是否符合条件
3. 类似于桶排序的思想，桶的大小为t+1,如果一个桶中出现两个数，则符合条件，所以每个桶最多只有一个元素，比较的时候，只需要和之前之后的桶进行比较即可

### 代码
```python
class Solution:
    def containsNearbyAlmostDuplicate(self, nums: List[int], k: int, t: int) -> bool:
        if t == 0 and len(nums) == len(set(nums)):
            return False
        if k == 0 or t < 0:
            return False
        for i, num in enumerate(nums):
            for j in range(i + 1, min(i + k + 1, len(nums))):
                if abs(num - nums[j]) <= t:
                    return True 
        return False
```
```
class Solution:
    def containsNearbyAlmostDuplicate(self, nums: List[int], k: int, t: int) -> bool:
        if t == 0 and len(nums) == len(set(nums)):
            return False
        if k == 0 or t < 0:
            return False
        bucket = {}
        n = len(nums)
        for i in range(n):
            m = nums[i] // (t + 1)
            if m in bucket:
                return True
            if m - 1 in bucket:
                if abs(nums[i] - bucket[m - 1]) <= t:
                    return True
            if m + 1 in bucket:
                if abs(nums[i] - bucket[m + 1]) <= t:
                    return True
            if i >= k:
                del bucket[nums[i - k] // (t + 1)]
            bucket[m] = nums[i]
        return False
```
