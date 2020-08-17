---
layout:     post
title:      LeetCode 1103 Distribute Candies to People (Python)
number:     1103
level:      Easy
lcurl:      distribute-candies-to-people
youtube:    XpPapD2oXgo
bilibili1:  //player.bilibili.com/player.html?aid=499352269&bvid=BV1jK411M75g&cid=225487553&page=1
xigua:      
date:       2020-08-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

We distribute some number of candies, to a row of n = num_people people in the following way:

We then give 1 candy to the first person, 2 candies to the second person, and so on until we give n candies to the last person.

Then, we go back to the start of the row, giving n + 1 candies to the first person, n + 2 candies to the second person, and so on until we give 2 * n candies to the last person.

This process repeats (with us giving one more candy each time, and moving to the start of the row after we reach the end) until we run out of candies.  The last person will receive all of our remaining candies (not necessarily one more than the previous gift).

Return an array (of length num_people and sum candies) that represents the final distribution of candies.

### 解题思路

先求出可以发满几轮，对于能发满的轮数，先把每个人能在这些轮拿到的总糖数算出来，最后一轮单独求每个人能拿到的糖数

### 代码
```python
class Solution:
    def distributeCandies(self, candies: int, num_people: int) -> List[int]:
        t = 0
        s = (1 + num_people) * num_people // 2
        cur = s
        while cur <= candies:
            t += 1
            cur += t * num_people * num_people + s
        res = [0] * num_people
        for i in range(num_people):
            res[i] = ((i+1) + ((i+1) + (t - 1) * num_people)) * t // 2
        candies -= sum(res)
        for i in range(num_people):
            tmp = min(candies, t * num_people + i + 1)
            res[i] += tmp
            candies -= tmp
        return res
```
