---
layout:     post
title:      LeetCode 45 Jump Game II (Python)
number:     45
level:      Medium
lcurl:      jump-game-ii
youtube:    2A1CkbghE6Y
bilibili1:  //player.bilibili.com/player.html?aid=630470156&bvid=BV1fb4y1Z77x&cid=334635942&page=1
xigua:      
date:       2021-05-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given an array of non-negative integers nums, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

You can assume that you can always reach the last index.

### 解题思路

相当于BFS，每次从上次可以跳到最远的地方到这次可以跳到最远的地方向后遍历，实现的时候只需要记录上次以及当前可以跳到最远的地方，遍历到上次可以跳到最远的地方之后，跳的次数加1

### 代码
```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        jump = curEnd = curFar = 0
        l = len(nums)
        for i in range(l - 1):
            curFar = max(curFar, i + nums[i])
            if curEnd == i:
                jump += 1
                curEnd = curFar
        return jump
```
