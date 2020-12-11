---
layout:     post
title:      LeetCode 80 Remove Duplicates from Sorted Array II (Python)
number:     80
level:      Medium
lcurl:      remove-duplicates-from-sorted-array-ii
youtube:    14wP2VSEx5M
bilibili1:  //player.bilibili.com/player.html?aid=798092310&bvid=BV1vy4y1S7sN&cid=265388107&page=1
xigua:      
date:       2020-12-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given a sorted array nums, remove the duplicates in-place such that duplicates appeared at most twice and return the new length.

Do not allocate extra space for another array; you must do this by modifying the input array in-place with O(1) extra memory.

### 解题思路

两个指针，一个遍历数，一个为最后返回的结果，如果当前的数与其之前的两个数不同，则保留这个数，将其复制到执行结果的指针出

### 代码
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i = 0
        for n in nums:
            if i < 2 or n != nums[i - 2]:
                nums[i] = n
                i += 1
        return i
```
