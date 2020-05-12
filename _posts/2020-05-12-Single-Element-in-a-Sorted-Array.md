---
layout:     post
title:      LeetCode 540 Single Element in a Sorted Array (Python)
number:     540
level:      Medium
lcurl:      single-element-in-a-sorted-array
youtube:    H0ZWQa2k-1E
bilibili1:  player.bilibili.com/player.html?aid=838164494&bvid=BV1Tg4y1B7Va&cid=190154460&page=1
xigua:      
date:       2020-05-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once. Find this single element that appears only once.

### 解题思路

二分，如果二分中点与两边的数不等，则是要找的数，我们来思考这样一列数`1 1 2 2 3 4 4 5 5`

如果二分到第一个2，它是在偶数位置，且与后面的数字相同，把左端点移动到中间

如果二分到第二个2，它是在奇数位置，且与前面的数字相同，把左端点移动到中间

另外两种情况移动右端点

### 代码
```python
class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1
        while l < r:
            mid = (l + r) // 2
            if nums[mid] != nums[mid-1] and nums[mid] != nums[mid+1]:
                return nums[mid]
            if (mid % 2 == 0 and nums[mid] == nums[mid+1]) or (mid % 2 == 1 and nums[mid] == nums[mid-1]):
                    l = mid + 1
            else:
                r = mid - 1
        return nums[l]
```
