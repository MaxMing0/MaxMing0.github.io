---
layout:     post
title:      LeetCode 735 Asteroid Collision (Python)
number:     735
level:      Medium
lcurl:      asteroid-collision
youtube:    RAGYf2tsCEY
bilibili1:  //player.bilibili.com/player.html?aid=927544609&bvid=BV1jT4y1F76n&cid=247985467&page=1
xigua:      
date:       2020-10-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

We are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

### 解题思路

使用栈，只有当栈顶元素向右，并且下一颗小行星向左的情况下，才会发生碰撞，再根据两颗小行星的大小分类讨论碰撞的结果

### 代码
```python
class Solution:
    def asteroidCollision(self, asteroids: List[int]) -> List[int]:
        stack = []
        for n in asteroids:
            if not stack or stack[-1] < 0 or n > 0:
                stack.append(n)
                continue
            while stack and stack[-1] > 0:
                if stack[-1] > abs(n):
                    break
                x = stack.pop()
                if x + n == 0:
                    break
            else:
                stack.append(n)
        return stack
```
