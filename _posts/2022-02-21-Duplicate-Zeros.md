---
layout:     post
title:      LeetCode 1089 Duplicate Zeros (Python)
number:     1089
level:      Easy
lcurl:      duplicate-zeros
youtube:    VpquvfB0PDA
bilibili1:  
xigua:      
date:       2022-02-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a fixed-length integer array arr, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything.

### 解题思路

遍历两次，第一次找到哪个数会放在数组的最后一位，如果最后是0可能写在最后一位或者两位，之后再向前遍历一次，把剩下的数填到数组中

### 代码
```python
class Solution:
    def duplicateZeros(self, arr: List[int]) -> None:
        """
        Do not return anything, modify arr in-place instead.
        """
        n, ct, cur, f = len(arr), 0, 0, False
        for num in arr:
            ct += 2 if num == 0 else 1
            if ct >= n:
                f = ct == n + 1
                break
            cur += 1

        right = n - 1
        if f:
            arr[-1] = 0
            cur -= 1
            right -= 1
        while cur >= 0:
            arr[right] = arr[cur]
            if arr[cur] == 0:
                arr[right - 1] = 0
                right -= 1    
            right -= 1
            cur -= 1
```
