---
layout:     post
title:      LeetCode 348 Design Tic-Tac-Toe (Python)
number:     348
level:      Medium
lcurl:      design-tic-tac-toe
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Assume the following rules are for the tic-tac-toe game on an n x n board between two players:

1. A move is guaranteed to be valid and is placed on an empty block.
2. Once a winning condition is reached, no more moves are allowed.
3. A player who succeeds in placing n of their marks in a horizontal, vertical, or diagonal row wins the game.
Implement the TicTacToe class:

- TicTacToe(int n) Initializes the object the size of the board n.
- int move(int row, int col, int player) Indicates that the player with id player plays at the cell (row, col) of the board. The move is guaranteed to be a valid move, and the two players alternate in making moves. Return
  - 0 if there is no winner after the move,
  - 1 if player 1 is the winner after the move, or
  - 2 if player 2 is the winner after the move.

### 解题思路

维护每一行，每一列，对角线，反对角线的总和，0player给对应的行列对角线-1，1player给对应的对角线+1，如果当前行列对角线为和的绝对值n，当前玩家获胜

### 代码
```python
class TicTacToe:

    def __init__(self, n: int):
        self.row = [0] * n
        self.col = [0] * n
        self.dig = 0
        self.adig = 0
        self.n = n

    def move(self, row: int, col: int, player: int) -> int:
        cur = 1 if player == 1 else -1
        self.row[row] += cur
        self.col[col] += cur
        if row == col:
            self.dig += cur
        if row + col == self.n - 1:
            self.adig += cur
        if abs(self.row[row]) == self.n or abs(self.col[col]) == self.n or abs(self.dig) == self.n or abs(self.adig) == self.n:
            return player
        return 0
        

# Your TicTacToe object will be instantiated and called as such:
# obj = TicTacToe(n)
# param_1 = obj.move(row,col,player)
```
