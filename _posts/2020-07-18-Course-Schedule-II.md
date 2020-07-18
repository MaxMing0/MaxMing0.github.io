---
layout:     post
title:      LeetCode 210 Course Schedule II (Python)
number:     210
level:      Medium
lcurl:      course-schedule-ii
youtube:    FbteISq1nqk
bilibili1:  //player.bilibili.com/player.html?aid=626496355&bvid=BV1qt4y1X7oC&cid=213849866&page=1
xigua:      
date:       2020-07-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Topological Sort
---

### 题目

There are a total of n courses you have to take, labeled from 0 to n-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, return the ordering of courses you should take to finish all courses.

There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all courses, return an empty array.

### 解题思路

根据前置课的要求建图，进行拓扑排序，方法是维护一个队里，存放所有入度为0的点

### 代码
```python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        indegree = [0] * numCourses
        edge = defaultdict(list)
        for x, y in prerequisites:
            indegree[x] += 1
            edge[y].append(x)
        q = [i for i in range(numCourses) if indegree[i] == 0]
        res = []
        while q:
            cur = q.pop()
            res.append(cur)
            for n in edge[cur]:
                indegree[n] -= 1
                if indegree[n] == 0:
                    q.append(n)
        return res if len(res) == numCourses else []
```
