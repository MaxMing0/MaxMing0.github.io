---
layout:     post
title:      LeetCode 554 Brick Wall (Python)
number:     554
level:      Medium
lcurl:      brick-wall
youtube:    -x-_WDuAFLs
bilibili1:  //player.bilibili.com/player.html?aid=375221630&bvid=BV1mo4y1f7wc&cid=328825386&page=1
xigua:      
date:       2021-04-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

There is a rectangular brick wall in front of you with n rows of bricks. The ith row has some number of bricks each of the same height (i.e., one unit) but they can be of different widths. The total width of each row is the same.

Draw a vertical line from the top to the bottom and cross the least bricks. If your line goes through the edge of a brick, then the brick is not considered as crossed. You cannot draw a line just along one of the two vertical edges of the wall, in which case the line will obviously cross no bricks.

Given the 2D array wall that contains the information about the wall, return the minimum number of crossed bricks after drawing such a vertical line.

### 解题思路

使用字典来存每一块儿砖分开的位置，最后去一个最小值

### 代码
```python
class Solution:
    def leastBricks(self, wall: List[List[int]]) -> int:
        dic = defaultdict(int)
        for row in wall:
            tmp = 0
            for c in row[:-1]:
                tmp += c
                dic[tmp] += 1
        if len(dic) == 0:
            return len(wall)
        return len(wall) - max(dic.values())
```
