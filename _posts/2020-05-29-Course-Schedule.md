---
layout:     post
title:      LeetCode 207 Course Schedule (Python)
number:     207
level:      Medium
lcurl:      course-schedule
youtube:    ZWaKl0_a6bU
bilibili1:  //player.bilibili.com/player.html?aid=200770298&bvid=BV1jz411B7UJ&cid=196393864&page=1
xigua:      
date:       2020-05-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
    - DFS
    - Topology Sort
---

### 题目

There are a total of numCourses courses you have to take, labeled from 0 to numCourses-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

### 解题思路

根据课程前置关系建立有向图，判断这个图是否存在环

### 代码
```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        inbound = [0] * numCourses
        edge = defaultdict(list)
        for x, y in prerequisites:
            inbound[x] += 1
            edge[y].append(x)
        q = [i for i in range(numCourses) if inbound[i] == 0]
        visited = 0
        while q:
            cur = q.pop()
            visited += 1  
            for n in edge[cur]:
                inbound[n] -= 1
                if inbound[n] == 0:
                    q.append(n)
        return  visited == numCourses
```
