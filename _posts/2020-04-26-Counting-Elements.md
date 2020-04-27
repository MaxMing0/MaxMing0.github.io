---
layout:     post
title:      LeetCode Counting Elements (Python)
number:     9999
level:      na
lcurl:      
youtube:    ax73iAm-9Ww
bilibili1:  //player.bilibili.com/player.html?aid=837663750&bvid=BV1Eg4y187vx&cid=175125793&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array arr, count element x such that x + 1 is also in arr.

If there're duplicates in arr, count them seperately.

### 解题思路



### 代码
```python
class Solution:
    def countElements(self, arr: List[int]) -> int:
        return len([0 for x in arr if (x + 1) in set(arr)])
```