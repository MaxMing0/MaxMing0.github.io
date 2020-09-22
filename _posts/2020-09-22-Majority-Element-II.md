---
layout:     post
title:      LeetCode 229 Majority Element II (Python)
number:     229
level:      Medium
lcurl:      majority-element-ii
youtube:    lGYHf_yMq7w
bilibili1:  //player.bilibili.com/player.html?aid=499667958&bvid=BV1nK411P7qR&cid=237897193&page=1
xigua:      
date:       2020-09-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.

Note: The algorithm should run in linear time and in O(1) space.

### 解题思路

摩尔投票算法，具体的过程，请参看视频

### 代码
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        if not nums:
            return []
        count1, count2, candidate1, candidate2 = 0, 0, None, None
        for n in nums:
            if candidate1 == n:
                count1 += 1
            elif candidate2 == n:
                count2 += 1
            elif count1 == 0:
                candidate1 = n
                count1 = 1
            elif count2 == 0:
                candidate2 = n
                count2 = 1
            else:
                count1 -= 1
                count2 -= 1
        res = []
        for c in [candidate1, candidate2]:
            if nums.count(c) > len(nums) // 3:
                res.append(c)
        return res
```
