---
layout:     post
title:      LeetCode 2300 Successful Pairs of Spells and Potions (Python)
number:     2300
level:      Medium
lcurl:      successful-pairs-of-spells-and-potions
youtube:    _EFiUxZE8mw
bilibili1:  
xigua:      
date:       2023-04-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
    - Two Pointers
---

### 题目

You are given two positive integer arrays spells and potions, of length n and m respectively, where spells[i] represents the strength of the ith spell and potions[j] represents the strength of the jth potion.

You are also given an integer success. A spell and potion pair is considered successful if the product of their strengths is at least success.

Return an integer array pairs of length n where pairs[i] is the number of potions that will form a successful pair with the ith spell.

### 解题思路

1. 对potion进行排序，对于每个spell，对potion进行二分找到有多少个的乘积小于success
2. 对spell和potion都进行排序，一个指针从最小的spell开始，一个指针从最大的potion开始，移动指针找到乘积小于success的位置

### 代码
```python
class Solution:
    def successfulPairs(self, spells: List[int], potions: List[int], success: int) -> List[int]:
        res = []
        m = len(potions)
        potions.sort()
        for s in spells:
            i = bisect.bisect_left(potions, math.ceil(success / s))
            res.append(m - i)
        return res
```
```python
class Solution:
    def successfulPairs(self, spells: List[int], potions: List[int], success: int) -> List[int]:
        spells = sorted([(s, i) for i, s in enumerate(spells)])
        potions.sort()
        res = [0] * len(spells)
        m = len(potions)
        j = m - 1
        for spell, i in spells:
            while j >= 0 and (spell * potions[j]) >= success:
                j -= 1
            res[i] = m - (j + 1)
        return res
```
