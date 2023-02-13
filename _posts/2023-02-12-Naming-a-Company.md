---
layout:     post
title:      LeetCode 2306 Naming a Company (Python)
number:     2306
level:      Hard
lcurl:      naming-a-company
youtube:    ECNCuRcLLqI
bilibili1:  
xigua:      
date:       2023-02-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an array of strings ideas that represents a list of names to be used in the process of naming a company. The process of naming a company is as follows:

Choose 2 distinct names from ideas, call them ideaA and ideaB.
Swap the first letters of ideaA and ideaB with each other.
If both of the new names are not found in the original ideas, then the name ideaA ideaB (the concatenation of ideaA and ideaB, separated by a space) is a valid company name.
Otherwise, it is not a valid name.
Return the number of distinct valid names for the company.

### 解题思路

将单词按照首字母进行分组，可以构成公司名字的单词必须来自两个不同组，所以遍历所有的首字母组合，然后看哪些单词后面的部分只在一边出现过，这样的单词就是合法的单词

### 代码
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        for i in range(n, 2 * n):
            secondNum = nums[i] << 10
            nums[i - n] |= secondNum

        allOnes = int(pow(2, 10)) - 1
        for i in range(n - 1, -1, -1):
            secondNum = nums[i] >> 10
            firstNum = nums[i] & allOnes
            nums[2 * i + 1] = secondNum
            nums[2 * i] = firstNum
        return nums
```
