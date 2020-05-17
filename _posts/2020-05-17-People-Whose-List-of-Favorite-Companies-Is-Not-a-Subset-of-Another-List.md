---
layout:     post
title:      LeetCode 1452 People Whose List of Favorite Companies Is Not a Subset of Another List (Python)
number:     1452
level:      Medium
lcurl:      people-whose-list-of-favorite-companies-is-not-a-subset-of-another-list
youtube:    c_JBfWVbsDY
bilibili1:  //player.bilibili.com/player.html?aid=285727482&bvid=BV1sf4y1U7K8&cid=192310295&page=1
xigua:      
date:       2020-05-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Set
---

### 题目

Given the array favoriteCompanies where favoriteCompanies[i] is the list of favorites companies for the ith person (indexed from 0).

Return the indices of people whose list of favorite companies is not a subset of any other list of favorites companies. You must return the indices in increasing order.

### 解题思路

把所有人喜爱的公司转换成set，遍历每个人，判断他喜欢的公司不是其它人的子集

### 代码
```python
class Solution:
    def peopleIndexes(self, favoriteCompanies: List[List[str]]) -> List[int]:
        s = [set(f) for f in favoriteCompanies]
        n = len(s)
        res = []
        for i in range(n):
            for j in range(n):
                if i != j and s[i].issubset(s[j]):
                    break
            else:
                res.append(i)
        return res
```
