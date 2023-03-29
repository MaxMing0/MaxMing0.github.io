---
layout:     post
title:      LeetCode 1402 Reducing Dishes (Python)
number:     1402
level:      Hard
lcurl:      reducing-dishes
youtube:    9TAOWffWJy8
bilibili1:  
xigua:      
date:       2023-03-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

A chef has collected data on the satisfaction level of his n dishes. Chef can cook any dish in 1 unit of time.

Like-time coefficient of a dish is defined as the time taken to cook that dish including previous dishes multiplied by its satisfaction level i.e. time[i] * satisfaction[i].

Return the maximum sum of like-time coefficient that the chef can obtain after dishes preparation.

Dishes can be prepared in any order and the chef can discard some dishes to get this maximum value.

### 解题思路

贪心，先做分低的，再做分高的，计算的时候先做分高的，每次再做一个菜的时候，加入之前所有菜分数之和，当所有菜分数之和为负数时，结束循环，

### 代码
```python
class Solution:
    def maxSatisfaction(self, satisfaction: List[int]) -> int:
        satisfaction.sort(reverse=True)
        res = tmp = 0
        for s in satisfaction:
            if tmp + s > 0:
                tmp += s
                res += tmp
            else:
                break
        return res
```
