---
layout:     post
title:      LeetCode 289 Game of Life (Python)
number:     289
level:      Medium
lcurl:      game-of-life
youtube:    y0iN99atfFo
bilibili1:  //player.bilibili.com/player.html?aid=970863411&bvid=BV1hp4y1B7D5&cid=272986693&page=1
xigua:      
date:       2020-12-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

According to Wikipedia's article: "The Game of Life, also known simply as Life, is a cellular automaton devised by the British mathematician John Horton Conway in 1970."

The board is made up of an m x n grid of cells, where each cell has an initial state: live (represented by a 1) or dead (represented by a 0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules (taken from the above Wikipedia article):

1. Any live cell with fewer than two live neighbors dies as if caused by under-population.
2. Any live cell with two or three live neighbors lives on to the next generation.
3. Any live cell with more than three live neighbors dies, as if by over-population.
4. Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.
The next state is created by applying the above rules simultaneously to every cell in the current state, where births and deaths occur simultaneously. Given the current state of the m x n grid board, return the next state.


**Follow up:**

- Could you solve it in-place? Remember that the board needs to be updated simultaneously: You cannot update some cells first and then use their updated values to update other cells.
- In this question, we represent the board using a 2D array. In principle, the board is infinite, which would cause problems when the active area encroaches upon the border of the array (i.e., live cells reach the border). How would you address these problems?

### 解题思路

按照题目要求模拟，in-place的做法：使用位运算，用高位来存新的状态，&1为当前的状态，最后将数组中每个数右移一位

### 代码
```python
class Solution:
    def gameOfLife(self, board: List[List[int]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        m = len(board)
        n = len(board[0])
        d = [(1, 0), (-1, 0), (0, 1), (0, -1), (-1, -1), (-1, 1), (1, -1), (1, 1)]
        for i in range(m):
            for j in range(n):
                live = 0
                for tx, ty in d:
                    x, y = i + tx, j + ty
                    if x < 0 or x == m or y < 0 or y == n:
                        continue
                    if board[x][y] & 1:
                        live += 1
                if board[i][j] == 0:
                    if live == 3:
                        board[i][j] = 2
                else:
                    if 2 <= live <= 3:
                        board[i][j] = 3
                    else:
                        board[i][j] = 1
        for i in range(m):
            for j in range(n):
                board[i][j] >>= 1
```
