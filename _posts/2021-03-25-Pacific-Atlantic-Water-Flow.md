---
layout:     post
title:      LeetCode 417 Pacific Atlantic Water Flow (Python)
number:     417
level:      Medium
lcurl:      pacific-atlantic-water-flow
youtube:    yqV65cfDmss
bilibili1:  //player.bilibili.com/player.html?aid=799797257&bvid=BV1by4y1h7ab&cid=315028723&page=1
xigua:      
date:       2021-03-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - BFS
---

### 题目

Given an m x n matrix of non-negative integers representing the height of each unit cell in a continent, the "Pacific ocean" touches the left and top edges of the matrix and the "Atlantic ocean" touches the right and bottom edges.

Water can only flow in four directions (up, down, left, or right) from a cell to another one with height equal or lower.

Find the list of grid coordinates where water can flow to both the Pacific and Atlantic ocean.

Note:

1. The order of returned grid coordinates does not matter.
2. Both m and n are less than 150.

### 解题思路

从上边和左边所有的点开始进行遍历，求出所有与太平洋相接的格，从下边和右边开始遍历，求出所有与大西洋相接的格子，结果做交集

### 代码
```python
class Solution:
    def dfs(self, matrix, q):
        m = len(matrix)
        n = len(matrix[0])
        ret = set([])
        directions = {(-1, 0), (1, 0), (0, -1), (0, 1)}
        while len(q) > 0:
            curx, cury = q.pop()
            ret.add((curx, cury))
            height = matrix[curx][cury]
            for dirx, diry in directions:
                tmpx, tmpy = dirx + curx, diry + cury
                if 0 <= tmpx < m and 0 <= tmpy < n and matrix[tmpx][tmpy] >= height:
                    if (tmpx, tmpy) not in ret:
                        q.append((tmpx, tmpy))
                        ret.add((tmpx, tmpy))
        return ret
    
    def pacificAtlantic(self, matrix: List[List[int]]) -> List[List[int]]:
        m = len(matrix)
        if m == 0:
            return []
        n = len(matrix[0])
        q = []
        for i in range(m):
            q.append((i, 0))
        for i in range(n):
            q.append((0, i))
        pac = self.dfs(matrix, q)

        q = []
        for i in range(m):
            q.append((i, n - 1))
        for i in range(n):
            q.append((m - 1, i))
        atl = self.dfs(matrix, q)

        res = pac.intersection(atl)
        return [list(x) for x in res]
```
