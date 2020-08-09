---
layout:     post
title:      LeetCode 994 Rotting Oranges (Python)
number:     994
level:      Medium
lcurl:      rotting-oranges
youtube:    dHgT3GWgUik
bilibili1:  //player.bilibili.com/player.html?aid=754147555&bvid=BV1Qk4y1m7fz&cid=222343986&page=1
xigua:      
date:       2020-08-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

In a given grid, each cell can have one of three values:

- the value 0 representing an empty cell;
- the value 1 representing a fresh orange;
- the value 2 representing a rotten orange.
Every minute, any fresh orange that is adjacent (4-directionally) to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange.  If this is impossible, return -1 instead.

### 解题思路

BFS，遍历整个格子，将所有烂橘子放到一个集合中，同时计算新鲜橘子的个数，每次从这个集合开始进行遍历，找到周围所有相邻的新鲜橘子加到一个临时集合中，时间+1

如果没有新的橘子变烂，则循环结束，最后判断新鲜橘子的个数是否为0

### 代码
```python
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        fresh = 0
        m, n = len(grid), len(grid[0])
        q = set()
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    fresh += 1
                elif grid[i][j] ==  2:
                    q.add((i, j))
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        res = 0
        while q:
            tmp = set()
            for curx, cury in q:
                for dirx, diry in directions:
                    tx, ty = curx + dirx, cury + diry
                    if 0 <= tx < m and 0 <= ty < n and grid[tx][ty] == 1:
                        tmp.add((tx, ty))
                        grid[tx][ty] = 2    
            q = tmp
            if q:
                res += 1
                fresh -= len(q)
        
        return res if fresh == 0 else -1
```
