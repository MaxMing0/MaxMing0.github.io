---
layout:     post
title:      LeetCode 179 Largest Number (Python)
number:     179
level:      Medium
lcurl:      largest-number
youtube:    H3rwSn8L3M4
bilibili1:  //player.bilibili.com/player.html?aid=414676312&bvid=BV1mV411m7aN&cid=238869514&page=1
xigua:      
date:       2020-09-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

Given a list of non negative integers, arrange them such that they form the largest number.

### 解题思路

将所有数字转换成字符串，ab两个数的大小为，比ab和ba的大小，将所有的数从大到小排列

### 代码
```python
class Compare(str):
    def __lt__(x, y):
        return x + y < y + x
    
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        largest_num = ''.join(sorted(map(str, nums), key=Compare, reverse=True))
        return '0' if largest_num[0] == '0' else largest_num
```
