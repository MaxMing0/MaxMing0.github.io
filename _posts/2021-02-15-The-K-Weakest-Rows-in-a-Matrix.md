---
layout:     post
title:      LeetCode 1337 The K Weakest Rows in a Matrix (Python)
number:     1337
level:      Easy
lcurl:      the-k-weakest-rows-in-a-matrix
youtube:    N8dnmKgg2yU
bilibili1:  //player.bilibili.com/player.html?aid=714158978&bvid=BV1bX4y157ju&cid=298007602&page=1
xigua:      
date:       2021-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a m * n matrix mat of ones (representing soldiers) and zeros (representing civilians), return the indexes of the k weakest rows in the matrix ordered from the weakest to the strongest.

A row i is weaker than row j, if the number of soldiers in row i is less than the number of soldiers in row j, or they have the same number of soldiers but i is less than j. Soldiers are always stand in the frontier of a row, that is, always ones may appear first and then zeros.

### 解题思路

先统计出来每一行有多少个士兵，然后连同行号一起放到堆里，pop出来前k个

### 代码
```python
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        power = []
        for r, row in enumerate(mat):
            tmp = 0
            for n in row:
                if n:
                    tmp += 1
                else:
                    break
            power.append((tmp, r))
        heapq.heapify(power)
        return [heapq.heappop(power)[1] for _ in range(k)]
```
