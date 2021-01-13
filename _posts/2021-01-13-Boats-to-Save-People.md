---
layout:     post
title:      LeetCode 881 Boats to Save People (Python)
number:     881
level:      Medium
lcurl:      boats-to-save-people
youtube:    TseMqUuQgeI
bilibili1:  //player.bilibili.com/player.html?aid=928686617&bvid=BV1MT4y1K7yq&cid=281897521&page=1
xigua:      
date:       2020-01-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

The i-th person has weight people[i], and each boat can carry a maximum weight of limit.

Each boat carries at most 2 people at the same time, provided the sum of the weight of those people is at most limit.

Return the minimum number of boats to carry every given person.  (It is guaranteed each person can be carried by a boat.)

### 解题思路

贪心，将数组从大到小排序，每次判断最大和最小的能否放到一个船里，如果可以放两个，不可以只放大的

### 代码
```python
class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        people.sort(reverse=True)
        i, j = 0, len(people) - 1
        while i <= j:
            if people[i] + people[j] <= limit:
                j -= 1
            i += 1
        return i
```
