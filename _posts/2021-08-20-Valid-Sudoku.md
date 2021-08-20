---
layout:     post
title:      LeetCode 36 Valid Sudoku (Python)
number:     36
level:      Medium
lcurl:      valid-sudoku
youtube:    oeMw30HapdQ
bilibili1:  //player.bilibili.com/player.html?aid=847478750&bvid=BV1ZL4y1e7oo&cid=393507011&page=1
xigua:      
date:       2021-08-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

1. Each row must contain the digits 1-9 without repetition.
2. Each column must contain the digits 1-9 without repetition.
3. Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
- Only the filled cells need to be validated according to the mentioned rules.


### 解题思路

用三个字典存每行每列和九宫格里出现的数，如果出现重复，返回false

### 代码
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        cols = defaultdict(lambda: set())
        rows = defaultdict(lambda: set())
        grids = defaultdict(lambda: set())
        for i in range(0,9):
            for j in range(0,9):
                if  board[i][j] == '.':
                    continue
                if board[i][j] in cols[j]:
                    return False
                cols[j].add(board[i][j])
                if board[i][j] in rows[i]:
                    return False
                rows[i].add(board[i][j])
                if board[i][j] in grids[10 * (i // 3) + j // 3]:
                    return False
                grids[10 * (i // 3) + j // 3].add(board[i][j])
        return True
```
