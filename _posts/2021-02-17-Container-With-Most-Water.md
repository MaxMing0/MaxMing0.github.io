---
layout:     post
title:      LeetCode 11 Container With Most Water (Python)
number:     11
level:      Medium
lcurl:      container-with-most-water
youtube:    a31GmDN_zEw
bilibili1:  //player.bilibili.com/player.html?aid=459150913&bvid=BV1A5411E7oM&cid=298822117&page=1
xigua:      
date:       2021-12-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

Notice that you may not slant the container.

### 解题思路

左右两个指针，计算能存的水，每次向内移动较矮的

### 代码
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        res = 0
        l, r = 0, len(height) - 1
        while l < r:
            res = max(res, min(height[r], height[l]) * (r - l))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        return res
```
