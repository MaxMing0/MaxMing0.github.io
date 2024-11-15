---
layout:     post
title:      LeetCode 1778 Shortest Path in a Hidden Grid (Python)
number:     1778
level:      Medium
lcurl:      shortest-path-in-a-hidden-grid
youtube:    
bilibili1:  
xigua:      
date:       2024-11-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - BFS
---

### 题目

This is an interactive problem.

There is a robot in a hidden grid, and you are trying to get it from its starting cell to the target cell in this grid. The grid is of size m x n, and each cell in the grid is either empty or blocked. It is guaranteed that the starting cell and the target cell are different, and neither of them is blocked.

You want to find the minimum distance to the target cell. However, you do not know the grid's dimensions, the starting cell, nor the target cell. You are only allowed to ask queries to the GridMaster object.

Thr GridMaster class has the following functions:

- boolean canMove(char direction) Returns true if the robot can move in that direction. Otherwise, it returns false.
- void move(char direction) Moves the robot in that direction. If this move would move the robot to a blocked cell or off the grid, the move will be ignored, and the robot will remain in the same position.
- boolean isTarget() Returns true if the robot is currently on the target cell. Otherwise, it returns false.
Note that direction in the above functions should be a character from {'U','D','L','R'}, representing the directions up, down, left, and right, respectively.

Return the minimum distance between the robot's initial starting cell and the target cell. If there is no valid path between the cells, return -1.

Custom testing:

The test input is read as a 2D matrix grid of size m x n where:

- grid[i][j] == -1 indicates that the robot is in cell (i, j) (the starting cell).
- grid[i][j] == 0 indicates that the cell (i, j) is blocked.
- grid[i][j] == 1 indicates that the cell (i, j) is empty.
- grid[i][j] == 2 indicates that the cell (i, j) is the target cell.
There is exactly one -1 and 2 in grid. Remember that you will not have this information in your code.

### 解题思路

先dfs，找到target，需要回溯，记录所有可以走的位置，再从起点进行bfs，找到最短路径

### 代码
```python
class Solution(object):
    target = None
    def findShortestPath(self, master: 'GridMaster') -> int:
        def dfs(curx, cury):
            if master.isTarget():
                self.target = (curx, cury)
            visit.add((curx, cury))
            for d in directions:
                nx, ny = curx + directions[d][0], cury + directions[d][1]
                if (nx, ny) not in visit and master.canMove(d):
                    master.move(d)
                    dfs(nx, ny)
                    master.move(rdirections[d])

        directions = {'U': (-1, 0), 'D': (1, 0), 'L': (0, -1), 'R': (0, 1)}
        rdirections = {'U': 'D', 'D': 'U', 'L': 'R', 'R': 'L'}
        visit = set()
        dfs(0, 0)
        if not self.target:
            return -1
        q = deque([(0, 0, 0)])
        visit.remove((0, 0))
        while q:
            curx, cury, step = q.popleft()
            if (curx, cury) == self.target:
                return step            
            for d in directions:
                nx, ny = curx + directions[d][0], cury + directions[d][1]
                if (nx, ny) in visit:
                    visit.remove((nx, ny))
                    q.append((nx, ny, step + 1))

```
