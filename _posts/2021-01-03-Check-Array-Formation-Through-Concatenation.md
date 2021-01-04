---
layout:     post
title:      LeetCode 1640 Check Array Formation Through Concatenation (Python)
number:     1640
level:      Easy
lcurl:      check-array-formation-through-concatenation
youtube:    OwR_btsuiy8
bilibili1:  //player.bilibili.com/player.html?aid=203528911&bvid=BV1uh411274P&cid=276843148&page=1
xigua:      
date:       2020-01-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an array of distinct integers arr and an array of integer arrays pieces, where the integers in pieces are distinct. Your goal is to form arr by concatenating the arrays in pieces in any order. However, you are not allowed to reorder the integers in each array pieces[i].

Return true if it is possible to form the array arr from pieces. Otherwise, return false.

### 解题思路

将所有pieces放到一个字典里，key是数组的第一个数，这样在遍历的时候就可以找到对应的piece，判断是否可以构成输入的数组

### 代码
```python
class Solution:
    def canFormArray(self, arr: List[int], pieces: List[List[int]]) -> bool:
        d = {x[0]: x for x in pieces}
        return list(chain(*[d.get(num, []) for num in arr])) == arr
```
