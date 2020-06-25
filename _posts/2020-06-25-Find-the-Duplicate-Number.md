---
layout:     post
title:      LeetCode 287 Find the Duplicate Number (Python)
number:     287
level:      Medium
lcurl:      find-the-duplicate-number
youtube:    OxJUxBSqU5k
bilibili1:  //player.bilibili.com/player.html?aid=838737795&bvid=BV1Ug4y1v7mF&cid=205625266&page=1
xigua:      
date:       2020-06-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two pointers
---

### 题目

Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

### 解题思路

通过位置i指向nums[i]的边建立一个图，因为有数字出现多次，那么这个图一定存在环，而且环的入口处就是重复的数，通过快慢指针的方法来找环的入口

### 代码
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = nums[0], nums[nums[0]]
        while slow != fast:
            slow = nums[slow]
            fast = nums[nums[fast]]
        slow = 0
        while slow != fast:
            slow = nums[slow]
            fast = nums[fast]
        return fast
```
