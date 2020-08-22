---
layout:     post
title:      LeetCode 497 Random Point in Non-overlapping Rectangles (Python)
number:     497
level:      Medium
lcurl:      random-point-in-non-overlapping-rectangles
youtube:    1lfAuryQYLg
bilibili1:  //player.bilibili.com/player.html?aid=884327312&bvid=BV12K4y1Y7r6&cid=227506803&page=1
xigua:      
date:       2020-08-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Random
    - Binary Search
---

### 题目

Given a list of non-overlapping axis-aligned rectangles rects, write a function pick which randomly and uniformily picks an integer point in the space covered by the rectangles.

Note:

1. An integer point is a point that has integer coordinates. 
2. A point on the perimeter of a rectangle is included in the space covered by the rectangles. 
3. ith rectangle = rects[i] = [x1,y1,x2,y2], where [x1, y1] are the integer coordinates of the bottom-left corner, and [x2, y2] are the integer coordinates of the top-right corner.
4. length and width of each rectangle does not exceed 2000.
5. 1 <= rects.length <= 100
6. pick return a point as an array of integer coordinates [p_x, p_y]
7. pick is called at most 10000 times.

### 解题思路

首先按照矩形覆盖整点的个数为权重取出一个矩形，然后再在这个矩形的范围内，随机横纵坐标

第一步可以先随机一个1到面积和的整数，使用二分来对应到矩形，或者使用`random.choices()`函数

### 代码
```python
class Solution:

    def __init__(self, rects: List[List[int]]):
        self.rects = rects
        rect = rects[0]
        self.areas = [(rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1)]
        for rect in rects[1:]:
            curarea = (rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1)
            self.areas.append(self.areas[-1] + curarea)
        self.sum = self.areas[-1]
            
    def pick(self) -> List[int]:
        ran = random.randint(1, self.sum)
        ind = bisect.bisect_left(self.areas, ran)
        rect = self.rects[ind]
        return [random.randint(rect[0], rect[2]), random.randint(rect[1], rect[3])]
```
```python
class Solution:

    def __init__(self, rects: List[List[int]]):
        self.rects = rects
        self.areas = [(rect[2] - rect[0] + 1) * (rect[3] - rect[1] + 1) for rect in rects]
            
    def pick(self) -> List[int]:
        rect = random.choices(population = self.rects, weights = self.areas)[0]
        return [random.randint(rect[0], rect[2]), random.randint(rect[1], rect[3])]
```
