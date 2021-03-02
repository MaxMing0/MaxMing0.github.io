---
layout:     post
title:      LeetCode 645 Set Mismatch (Python)
number:     645
level:      Easy
lcurl:      set-mismatch
youtube:    aHadvFUHHL0
bilibili1:  //player.bilibili.com/player.html?aid=289429683&bvid=BV1Pf4y1479j&cid=305089971&page=1
xigua:      
date:       2021-03-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return them in the form of an array.

### 解题思路

求出所有不同数的总和，重复数为总和减去不同数的总和，缺失的数为1到n的和，减去不同数的总和

### 代码
```python
class Solution:
    def findErrorNums(self, nums: List[int]) -> List[int]:
        sum_unique = sum(set(nums))
        dup = sum(nums) - sum_unique
        miss = (len(nums) + 1) * len(nums) // 2 - sum_unique 
        return [dup, miss]
```
