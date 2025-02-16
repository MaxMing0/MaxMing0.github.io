---
layout:     post
title:      LeetCode 489 Robot Room Cleaner (Python)
number:     489
level:      Hard
lcurl:      robot-room-cleaner
youtube:    
bilibili1:  
xigua:      
date:       2025-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - backtracking
---

### 题目

You are controlling a robot that is located somewhere in a room. The room is modeled as an m x n binary grid where 0 represents a wall and 1 represents an empty slot.

The robot starts at an unknown location in the room that is guaranteed to be empty, and you do not have access to the grid, but you can move the robot using the given API Robot.

You are tasked to use the robot to clean the entire room (i.e., clean every empty cell in the room). The robot with the four given APIs can move forward, turn left, or turn right. Each turn is 90 degrees.

When the robot tries to move into a wall cell, its bumper sensor detects the obstacle, and it stays on the current cell.

### 解题思路

记录所有走过的位置，递归的时候记录方向，逆时针走，两个右转，向前，再两个右转可以回退。

### 代码
```python
#
# """
# This is the robot's control interface.
# You should not implement it, or speculate about its implementation
# """
#class Robot:
#    def move(self):
#        """
#        Returns true if the cell in front is open and robot moves into the cell.
#        Returns false if the cell in front is blocked and robot stays in the current cell.
#        :rtype bool
#        """
#
#    def turnLeft(self):
#        """
#        Robot will stay in the same cell after calling turnLeft/turnRight.
#        Each turn will be 90 degrees.
#        :rtype void
#        """
#
#    def turnRight(self):
#        """
#        Robot will stay in the same cell after calling turnLeft/turnRight.
#        Each turn will be 90 degrees.
#        :rtype void
#        """
#
#    def clean(self):
#        """
#        Clean the current cell.
#        :rtype void
#        """

class Solution:
    def cleanRoom(self, robot):
        """
        :type robot: Robot
        :rtype: None
        """
        def back():
            robot.turnRight()
            robot.turnRight()
            robot.move()
            robot.turnRight()
            robot.turnRight()

        def dfs(x, y, d):
            visit.add((x, y))
            robot.clean()
            for i in range(4):
                td = (d + i) % 4
                tx, ty = x + directions[td][0], y + directions[td][1]
                if (tx, ty) not in visit and robot.move():
                    dfs(tx, ty, td)
                    back()
                robot.turnRight()
        directions = [(-1, 0), (0, 1), (1, 0), (0, -1)]
        visit = set()
        dfs(0, 0, 0)
```
