---
layout:     post
title:      LeetCode 228 Summary Ranges (Python)
number:     228
level:      Easy
lcurl:      summary-ranges
youtube:    nIdUN_uIUTM
bilibili1:  //player.bilibili.com/player.html?aid=627509075&bvid=BV1Et4y1i7YZ&cid=250317061&page=1
xigua:      
date:       2020-10-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given a sorted unique integer array nums.

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

- "a->b" if a != b
- "a" if a == b

### 解题思路

记录区间起点位置，如果后一个数与当前数字不相邻，则前一段形成一个区间，分别处理一个元素和多个元素的情况

### 代码
```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        l = len(nums)
        if l == 0:
            return []
        nums.append(float('inf'))
        res, start = [], 0
        for i in range(l):
            if nums[i + 1] != nums[i] + 1:
                res.append(str(nums[i]) if i == start else "%s->%s" % (nums[start], nums[i]))
                start = i + 1
        return res
```
