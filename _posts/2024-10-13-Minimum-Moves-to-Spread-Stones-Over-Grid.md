---
layout:     post
title:      LeetCode 2850 Minimum Moves to Spread Stones Over Grid (Python)
number:     2850
level:      Medium
lcurl:      minimum-moves-to-spread-stones-over-grid
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

You are given a 0-indexed 2D integer matrix grid of size 3 * 3, representing the number of stones in each cell. The grid contains exactly 9 stones, and there can be multiple stones in a single cell.

In one move, you can move a single stone from its current cell to any other cell if the two cells share a side.

Return the minimum number of moves required to place one stone in each cell.

### 解题思路

把3*3的格表示成长度为9的tuple，从初始状态开始bfs，结果要求全1，bfs的时候要求只能从数字大的向数字小的移动1，只有大于1的可以移动

### 代码
```python
class Solution:
    def minimumMoves(self, grid: List[List[int]]) -> int:
        state = []
        for i in range(3):
            for j in range(3):
                state.append(grid[i][j])
        q = [tuple(state)]
        visited = {tuple(state)}
        res = 0
        target = (1,1,1,1,1,1,1,1,1)
        while q:
            tmp = []
            for state in q:
                if state == target:
                    return res
                state = list(state)
                for i in range(9):
                    if state[i] > 1:
                        cx, cy = i // 3, i % 3
                        for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                            nx, ny = cx + dx, cy + dy
                            if 0<=nx<=2 and 0<=ny<=2 and state[i] > state[nx*3+ny]:
                                cstate = state[:]
                                cstate[i] -= 1
                                cstate[nx*3+ny] += 1
                                tpstate = tuple(cstate)
                                if tpstate not in visited:
                                    visited.add(tpstate)
                                    tmp.append(tpstate)
            q = tmp[:]
            res += 1
        return 0
```
