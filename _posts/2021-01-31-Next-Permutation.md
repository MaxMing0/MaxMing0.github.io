---
layout:     post
title:      LeetCode 31 Next Permutation (Python)
number:     31
level:      Medium
lcurl:      next-permutation
youtube:    QyGf6JhF_mc
bilibili1:  //player.bilibili.com/player.html?aid=586462744&bvid=BV1Uz4y1m72N&cid=290753993&page=1
xigua:      
date:       2021-01-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

The replacement must be in place and use only constant extra memory.

### 解题思路

从后向前遍历找到第一个升序的位置，再次从后向前遍历找到第一个比它大的数，进行交换，再对后面的数排序，如果没有升序的位置，将数组返序

### 代码
```python
class Solution:
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        i = n - 2
        while i >= 0:
            if nums[i] >= nums[i + 1]:
                i -= 1
            else:
                for j in range(n - 1, i, -1):
                    if nums[j] > nums[i]:
                        nums[i], nums[j] = nums[j], nums[i]
                        nums[i + 1:] = sorted(nums[i + 1:])
                        return
        nums.reverse()
```
