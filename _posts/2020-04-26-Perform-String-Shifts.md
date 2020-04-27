---
layout:     post
title:      LeetCode Perform String Shifts (Python)
number:     9999
level:      na
lcurl:      
youtube:    UY3taCEB-Lo
bilibili1:  //player.bilibili.com/player.html?aid=925337397&bvid=BV1uT4y1V7G4&cid=178274405&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given a string s containing lowercase English letters, and a matrix shift, where shift[i] = [direction, amount]:

- direction can be 0 (for left shift) or 1 (for right shift). 
- amount is the amount by which string s is to be shifted.
- A left shift by 1 means remove the first character of s and append it to the end.
- Similarly, a right shift by 1 means remove the last character of s and add it to the beginning.

Return the final string after all operations.

### 解题思路



### 代码
```python
class Solution:
    def stringShift(self, s: str, shift: List[List[int]]) -> str:
        final_shift = 0
        for direction, amount in shift:
            if direction:
                final_shift += amount
            else:
                final_shift -= amount
        final_shift %= len(s)
        return s[-final_shift:] + s[:-final_shift]
```