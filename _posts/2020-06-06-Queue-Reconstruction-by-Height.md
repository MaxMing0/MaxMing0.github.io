---
layout:     post
title:      LeetCode 406 Queue Reconstruction by Height (Python)
number:     406
level:      Medium
lcurl:      queue-reconstruction-by-height
youtube:    LnxOUvwZkYo
bilibili1:  //player.bilibili.com/player.html?aid=795978110&bvid=BV1xC4y1a72W&cid=199235672&page=1
xigua:      
date:       2020-06-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers (h, k), where h is the height of the person and k is the number of people in front of this person who have a height greater than or equal to h. Write an algorithm to reconstruct the queue.

Note:
The number of people is less than 1,100.

### 解题思路

贪心，按照身高从高到低排序，身高相同则按位置从小到大排序，因为无论矮的人排在哪里，都不会影响高的人，所以就按照排序的结果，按顺序把每个人插入到相应的位置

### 代码
```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        people.sort(key = lambda x: (-x[0], x[1]))
        res = []
        for p in people:
            res.insert(p[1], p)
        return res
```
