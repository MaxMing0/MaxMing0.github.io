---
layout:     post
title:      LeetCode 957 Prison Cells After N Days (Python)
number:     957
level:      Medium
lcurl:      prison-cells-after-n-days
youtube:    https://youtu.be/poLwhq5DEvc
bilibili1:  //player.bilibili.com/player.html?aid=328687969&bvid=BV1qA411i7P4&cid=208395853&page=1
xigua:      
date:       2020-07-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

There are 8 prison cells in a row, and each cell is either occupied or vacant.

Each day, whether the cell is occupied or vacant changes according to the following rules:

- If a cell has two adjacent neighbors that are both occupied or both vacant, then the cell becomes occupied.
- Otherwise, it becomes vacant.
(Note that because the prison is a row, the first and the last cells in the row can't have two adjacent neighbors.)

We describe the current state of the prison in the following way: cells[i] == 1 if the i-th cell is occupied, else cells[i] == 0.

Given the initial state of the prison, return the state of the prison after N days (and N such changes described above.)

### 解题思路

先找到状态的循环，直接找到最后的状态

### 代码
```python
class Solution:
    def prisonAfterNDays(self, cells: List[int], N: int) -> List[int]:
        dic = {}
        while N > 0:
            dic[''.join(map(str, cells))] = N
            N -= 1
            tmp = [0] * 8
            for i in range(1, 7):
                tmp[i] = 1 if cells[i - 1] == cells[i + 1] else 0
            cells = tmp
            t = ''.join(map(str, cells))
            if t in dic:
                N = N % (dic[t] - N)
        return cells
```
```python
class Solution:
    def prisonAfterNDays(self, cells: List[int], N: int) -> List[int]:
        def find(cells):
            tmp = [0] * 8
            for i in range(1, 7):
                tmp[i] = 1 if cells[i - 1] == cells[i + 1] else 0
            return tmp
        
        cycle = []
        state = find(cells)
        while state not in cycle:
            cycle.append(state)
            state = find(state)
        return cycle[(N - 1) % len(cycle)]
```
