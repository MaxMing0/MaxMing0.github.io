---
layout:     post
title:      LeetCode 130 Surrounded Regions (Python)
number:     130
level:      Medium
lcurl:      surrounded-regions
youtube:    -5xOQLBJ8dY
bilibili1:  //player.bilibili.com/player.html?aid=413620512&bvid=BV1pV411k7TH&cid=202916429&page=1
xigua:      
date:       2020-06-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - BSF
---

### 题目

Given a 2D board containing 'X' and 'O' (the letter O), capture all regions surrounded by 'X'.

A region is captured by flipping all 'O's into 'X's in that surrounded region.

### 解题思路

先把一圈的所有O，找出来，从这些位置开始搜索，把所有相邻的O找出来，其它所有位置换成X

### 代码
```python
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        if not board:
            return
        m, n = len(board), len(board[0])
        stack = []
        for i in range(m):
            if board[i][0] == 'O':
                stack.append((i, 0))
            if board[i][n - 1] == 'O':
                stack.append((i, n - 1))
        for i in range(1, n - 1):
            if board[0][i] == 'O':
                stack.append((0, i))
            if board[m - 1][i] == 'O':
                stack.append((m - 1, i))
        while stack:
            i, j = stack.pop()
            if 0 <= i < m and 0 <= j < n and board[i][j] == 'O':
                board[i][j] = "#"
                stack += (i, j - 1), (i, j + 1), (i - 1, j), (i + 1, j)
        board[:] = [['XO'[c == '#'] for c in row] for row in board]
```
