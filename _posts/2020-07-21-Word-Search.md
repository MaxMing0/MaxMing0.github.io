---
layout:     post
title:      LeetCode 79 Word Search (Python)
number:     79
level:      Medium
lcurl:      word-search
youtube:    Z8imYXpqC5Q
bilibili1:  //player.bilibili.com/player.html?aid=371467388&bvid=BV1iZ4y1T78D&cid=214982330&page=1
xigua:      
date:       2020-07-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Backtracking
---

### 题目

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

### 解题思路

遍历整个board，如果和要找的单词的第一个字母相同，就开始递归回溯

### 代码
```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        def dfs(x, y, p):
            if p == l:
                return True
            for dirx, diry in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
                curx, cury = x + dirx, y + diry
                if 0 <= curx < m and 0 <= cury < n and flag[curx][cury] and board[curx][cury] == word[p]:
                    flag[curx][cury] = False
                    if dfs(curx, cury, p + 1):
                        flag[curx][cury] = True
                        return True
                    flag[curx][cury] = True
            return False
        
        m, n = len(board), len(board[0])
        l = len(word)
        flag = [[True] * n for _ in range(m)]
        for i in range(m):
            for j in range(n):
                if board[i][j] == word[0]:
                    flag[i][j] = False
                    if dfs(i, j, 1):
                        return True
                    flag[i][j] = True
        return False
```
