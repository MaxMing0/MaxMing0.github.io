---
layout:     post
title:      LeetCode 733 Flood Fill (Python)
number:     733
level:      Easy
lcurl:      flood-fill
youtube:    muVS7mUeq6g
bilibili1:  //player.bilibili.com/player.html?aid=370677462&bvid=BV1HZ4y1p7vH&cid=189782190&page=1
xigua:      
date:       2020-05-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

An image is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate (sr, sc) representing the starting pixel (row and column) of the flood fill, and a pixel value newColor, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

### 解题思路

DFS或者BFS，从给定的点开始，找四周颜色相同的点，并涂上新的颜色

### 代码
```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        m, n = len(image), len(image[0])
        directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
        q = [(sr, sc)]
        visited = {(sr, sc)}
        color = image[sr][sc]
        while q:
            x, y = q.pop()
            image[x][y] = newColor
            for dirx, diry in directions:
                tx, ty = x + dirx, y + diry
                if 0 <= tx < m and 0 <= ty < n and image[tx][ty] == color and (tx, ty) not in visited:
                    q.append((tx, ty))
                    visited.add((tx, ty))
        return image
```
