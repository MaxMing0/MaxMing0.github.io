---
layout:     post
title:      LeetCode 593 Valid Square (Python)
number:     593
level:      Medium
lcurl:      valid-square
youtube:    5NzFt_qdNbA
bilibili1:  //player.bilibili.com/player.html?aid=457724942&bvid=BV1j5411V73U&cid=254744474&page=1
xigua:      
date:       2020-11-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

源代码以及文字版解题思路 https://maxming0.github.io/2020/11/11/Valid-Square/
YouTube: https://www.youtube.com/channel/UCdSmtAmcHSc-V-5FhVidFrQ
bilibili: https://space.bilibili.com/478428905
如果喜欢我的视频，请订阅我的频道哦

### 解题思路

如果能构成正方形，要求四个边的长度相等，对角线的长度相等，且均不为0

### 代码
```python
class Solution:
    def validSquare(self, p1: List[int], p2: List[int], p3: List[int], p4: List[int]) -> bool:
        dis = []
        dis.append((p1[0] - p2[0]) ** 2 + (p1[1] - p2[1]) ** 2)
        dis.append((p1[0] - p3[0]) ** 2 + (p1[1] - p3[1]) ** 2)
        dis.append((p1[0] - p4[0]) ** 2 + (p1[1] - p4[1]) ** 2)
        dis.append((p2[0] - p3[0]) ** 2 + (p2[1] - p3[1]) ** 2)
        dis.append((p2[0] - p4[0]) ** 2 + (p2[1] - p4[1]) ** 2)
        dis.append((p3[0] - p4[0]) ** 2 + (p3[1] - p4[1]) ** 2)
        dis.sort()
        return dis[0] != 0 and dis[0] == dis[1] == dis[2] == dis[3] and dis[4] == dis[5]
```
