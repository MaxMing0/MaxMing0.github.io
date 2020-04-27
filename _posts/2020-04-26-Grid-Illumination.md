---
layout:     post
title:      LeetCode 1001 Grid Illumination (Python)
number:     1001
level:      Hard
lcurl:      grid-illumination
youtube:    1eFr5hV6MmQ
bilibili1:  //player.bilibili.com/player.html?aid=925358972&bvid=BV1NT4y1V7Vk&cid=180733490&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

On a N x N grid of cells, each cell (x, y) with 0 <= x < N and 0 <= y < N has a lamp.

Initially, some number of lamps are on.  lamps[i] tells us the location of the i-th lamp that is on.  Each lamp that is on illuminates every square on its x-axis, y-axis, and both diagonals (similar to a Queen in chess).

For the i-th query queries[i] = (x, y), the answer to the query is 1 if the cell (x, y) is illuminated, else 0.

After each query (x, y) [in the order given by queries], we turn off any lamps that are at cell (x, y) or are adjacent 8-directionally (ie., share a corner or edge with cell (x, y).)

Return an array of answers.  Each value answer[i] should be equal to the answer of the i-th query queries[i].

### 解题思路



### 代码
```python
from collections import defaultdict
class Solution:
    def gridIllumination(self, N: int, lamps: List[List[int]], queries: List[List[int]]) -> List[int]:
        ctx = defaultdict(int)
        cty = defaultdict(int)
        ctd = defaultdict(int)
        ctad = defaultdict(int)
        res = []
        s = set([tuple(x) for x in lamps])
        for x, y in lamps:
            ctx[x] += 1
            cty[y] += 1
            ctd[x + y] += 1
            ctad[x - y] += 1
        directions = [(-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 0), (0, 1), (1, -1), (1, 0), (1, 1)]
        for x, y in queries:
            if ctx[x] > 0 or cty[y] or ctd[x + y] > 0 or ctad[x - y] > 0:
                res.append(1)
            else:
                res.append(0)
            for dirx, diry in directions:
                p, q = x + dirx, y + diry
                if (p, q) in s:
                    s.remove((p, q))
                    ctx[p] -= 1
                    cty[q] -= 1
                    ctd[p + q] -= 1
                    ctad[p - q] -= 1
        return res
```