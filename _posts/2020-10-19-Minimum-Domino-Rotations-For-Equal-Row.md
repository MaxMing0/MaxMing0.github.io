---
layout:     post
title:      LeetCode 1007 Minimum Domino Rotations For Equal Row (Python)
number:     1007
level:      Medium
lcurl:      minimum-domino-rotations-for-equal-row
youtube:    2Q443COCp88
bilibili1:  //player.bilibili.com/player.html?aid=755113829&bvid=BV1br4y1w7TM&cid=247311241&page=1
xigua:      
date:       2020-10-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

In a row of dominoes, A[i] and B[i] represent the top and bottom halves of the ith domino.  (A domino is a tile with two numbers from 1 to 6 - one on each half of the tile.)

We may rotate the ith domino, so that A[i] and B[i] swap values.

Return the minimum number of rotations so that all the values in A are the same, or all the values in B are the same.

If it cannot be done, return -1.

### 解题思路

如果答案存在，那么答案一定是第一个骨牌上面的数或者下面的数，分别计算把所有骨牌都转成和这两个数在上面相同或者在下面相同，所需的旋转次数，返回最小值

### 代码
```python
class Solution:
    def minDominoRotations(self, A: List[int], B: List[int]) -> int:
        def check(n):
            reta = retb = 0
            for i in range(len(A)):
                if A[i] != n and B[i] != n:
                    return -1
                if A[i] != n:
                    reta += 1
                elif B[i] != n:
                    retb += 1
            return min(reta, retb)
        
        res = check(A[0])
        if res != -1 or A[0] == B[0]:
            return res
        return check(B[0])
```
