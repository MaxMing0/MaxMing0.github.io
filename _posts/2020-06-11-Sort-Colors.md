---
layout:     post
title:      LeetCode 75 Sort Colors (Python)
number:     75
level:      Medium
lcurl:      sort-colors
youtube:    kln9xC6GGYQ
bilibili1:  //player.bilibili.com/player.html?aid=668392707&bvid=BV1ua4y1v7yd&cid=200898050&page=1
xigua:      
date:       2020-06-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Note: You are not suppose to use the library's sort function for this problem.

### 解题思路

维护三个指针，p0指向0的最右边，p2指向2的最左边，p1指向当前位置，如果p1指向的是0和p0交换，是2和p2交换，是1则继续

### 代码
```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        p0, p1, p2 = 0, 0, len(nums) - 1
        while p1 <= p2:
            if nums[p1] == 0:
                nums[p0], nums[p1] = nums[p1], nums[p0]
                p0 += 1
                p1 += 1
            elif nums[p1] == 2:
                nums[p1], nums[p2] = nums[p2], nums[p1]
                p2 -= 1
            else:
                p1 += 1
```
