---
layout:     post
title:      LeetCode 799 Champagne Tower (Python)
number:     799
level:      Medium
lcurl:      champagne-tower
youtube:    vXtDHAGzZlI
bilibili1:  //player.bilibili.com/player.html?aid=202624703&bvid=BV1Da411A7u5&cid=249701840&page=1
xigua:      
date:       2020-10-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

We stack glasses in a pyramid, where the first row has 1 glass, the second row has 2 glasses, and so on until the 100th row.  Each glass holds one cup (250ml) of champagne.

Then, some champagne is poured in the first glass at the top.  When the topmost glass is full, any excess liquid poured will fall equally to the glass immediately to the left and right of it.  When those glasses become full, any excess champagne will fall equally to the left and right of those glasses, and so on.  (A glass at the bottom row has its excess champagne fall on the floor.)

For example, after one cup of champagne is poured, the top most glass is full.  After two cups of champagne are poured, the two glasses on the second row are half full.  After three cups of champagne are poured, those two cups become full - there are 3 full glasses total now.  After four cups of champagne are poured, the third row has the middle glass half full, and the two outside glasses are a quarter full, as pictured below.

Now after pouring some non-negative integer cups of champagne, return how full the jth glass in the ith row is (both i and j are 0-indexed.)

### 解题思路

模拟，对于在(r, c)的杯，如果慢了会流到(r + 1, c) (r + 1, c + 1)的杯子中，只需要记录某个杯子会收到多少酒，计算出会流到下面的两个杯子多少酒

### 代码
```python
class Solution:
    def champagneTower(self, poured: int, query_row: int, query_glass: int) -> float:
        q = [poured]
        for r in range(query_row):
            q2 = [0] * (len(q) + 1)
            for i, amount in enumerate(q):
                if amount <= 1:
                    continue
                tmp = (amount - 1) / 2
                q2[i] += tmp
                q2[i + 1] += tmp
            q = q2
        return min(q[query_glass], 1)
```
