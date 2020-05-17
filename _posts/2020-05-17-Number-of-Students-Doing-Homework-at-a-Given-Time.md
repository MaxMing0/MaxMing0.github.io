---
layout:     post
title:      LeetCode 1450 Number of Students Doing Homework at a Given Time (Python)
number:     1450
level:      Easy
lcurl:      number-of-students-doing-homework-at-a-given-time
youtube:    5u81osc9liw
bilibili1:  //player.bilibili.com/player.html?aid=243163149&bvid=BV1Ne411W7kS&cid=192307098&page=1
xigua:      
date:       2020-05-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given two integer arrays startTime and endTime and given an integer queryTime.

The ith student started doing their homework at the time startTime[i] and finished it at time endTime[i].

Return the number of students doing their homework at time queryTime. More formally, return the number of students where queryTime lays in the interval [startTime[i], endTime[i]] inclusive.

### 解题思路

遍历每个学生开始和结束做作业的时间，判断是否包含查询时刻

### 代码
```python
class Solution:
    def busyStudent(self, startTime: List[int], endTime: List[int], queryTime: int) -> int:
        res = 0
        for s, e in zip(startTime, endTime):
            if s <= queryTime <= e:
                res += 1
        return res
```
