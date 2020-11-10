---
layout:     post
title:      LeetCode 832 Flipping an Image (Python)
number:     832
level:      Easy
lcurl:      flipping-an-image
youtube:    -gHgV5SeNzI
bilibili1:  //player.bilibili.com/player.html?aid=842668638&bvid=BV1q54y1r7f3&cid=254453439&page=1
xigua:      
date:       2020-11-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

### 解题思路

对于每行中的第i个位置，与-(i+1)=~i，位置进行交换，与1进行异或，进行翻转

### 代码
```python
class Solution:
    def flipAndInvertImage(self, A: List[List[int]]) -> List[List[int]]:
        for row in A:
            for i in range((len(row) + 1) // 2):
                row[i], row[~i] = row[~i] ^ 1, row[i] ^ 1
        return A
```
