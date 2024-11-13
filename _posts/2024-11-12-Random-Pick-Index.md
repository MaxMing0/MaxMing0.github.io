---
layout:     post
title:      LeetCode 398 Random Pick Index (Python)
number:     398
level:      Medium
lcurl:      random-pick-index
youtube:    
bilibili1:  
xigua:      
date:       2024-11-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
---

### 题目

Given an integer array nums with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.

Implement the Solution class:

Solution(int[] nums) Initializes the object with the array nums.
int pick(int target) Picks a random index i from nums where nums[i] == target. If there are multiple valid i's, then each index should have an equal probability of returning.

### 解题思路

使用字典存每个数字出现的所有位置，用random.choice随机选取这个数字出现的位置

### 代码
```python
class Solution:

    def __init__(self, nums: List[int]):
        self.dic = defaultdict(list)
        for i, n in enumerate(nums):
            self.dic[n].append(i)

    def pick(self, target: int) -> int:
        return random.choice(self.dic[target])
```
