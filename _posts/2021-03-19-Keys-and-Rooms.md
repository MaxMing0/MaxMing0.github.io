---
layout:     post
title:      LeetCode 841 Keys and Rooms (Python)
number:     841
level:      Medium
lcurl:      keys-and-rooms
youtube:    INdwm-tXkHY
bilibili1:  //player.bilibili.com/player.html?aid=629714641&bvid=BV1Wb4y1Q7hE&cid=312773061&page=1
xigua:      
date:       2021-03-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

There are N rooms and you start in room 0.  Each room has a distinct number in 0, 1, 2, ..., N-1, and each room may have some keys to access the next room. 

Formally, each room i has a list of keys rooms[i], and each key rooms[i][j] is an integer in [0, 1, ..., N-1] where N = rooms.length.  A key rooms[i][j] = v opens the room with number v.

Initially, all the rooms start locked (except for room 0). 

You can walk back and forth between rooms freely.

Return true if and only if you can enter every room.

### 解题思路

从第0号房间进行BFS或者DFS，统计所有可以访问到的房间是否为总房间数

### 代码
```python
class Solution:
    def canVisitAllRooms(self, rooms: List[List[int]]) -> bool:
        s = set([0])
        q = [0]
        while q:
            cur = q.pop()
            for n in rooms[cur]:
                if n not in s:
                    q.append(n)
                    s.add(n)
        return len(s) == len(rooms)
```
