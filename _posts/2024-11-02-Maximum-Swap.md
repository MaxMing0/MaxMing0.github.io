---
layout:     post
title:      LeetCode 670 Maximum Swap (Python)
number:     670
level:      Medium
lcurl:      maximum-swap
youtube:    
bilibili1:  
xigua:      
date:       2024-11-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given an integer num. You can swap two digits at most once to get the maximum valued number.

Return the maximum valued number you can get.

### 解题思路

维护两个位置，从右向左进行遍历，分别记录遇到的最大数，和遇到的最后一比最大数小的数，对这两个数进行交换，如果没有比最大数小的数，返回初始的数

### 代码
```python
class Solution:
    def maximumSwap(self, num: int) -> int:
        lnum = list(str(num))
        n = len(lnum)
        idx = n - 1
        sl = sr = -1
        md = " "
        for i in range(n - 1, -1, -1):
            if lnum[i] > md:
                md = lnum[i]
                idx = i
            if lnum[i] < md:
                sl = i
                sr = idx
        if sl == -1:
            return num
        lnum[sl], lnum[sr] = lnum[sr], lnum[sl]
        return int("".join(lnum))
```
