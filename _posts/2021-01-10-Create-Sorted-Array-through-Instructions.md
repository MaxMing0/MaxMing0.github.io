---
layout:     post
title:      LeetCode 1649 Create Sorted Array through Instructions (Python)
number:     1649
level:      Hard
lcurl:      create-sorted-array-through-instructions
youtube:    LkiEe_ja2Ak
bilibili1:  
xigua:      
date:       2021-01-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Index Tree
---

### 题目

Given an integer array instructions, you are asked to create a sorted array from the elements in instructions. You start with an empty container nums. For each element from left to right in instructions, insert it into nums. The cost of each insertion is the minimum of the following:

- The number of elements currently in nums that are strictly less than instructions[i].
- The number of elements currently in nums that are strictly greater than instructions[i].
For example, if inserting element 3 into nums = [1,2,3,5], the cost of insertion is min(2, 1) (elements 1 and 2 are less than 3, element 5 is greater than 3) and nums will become [1,2,3,3,5].

Return the total cost to insert all elements from instructions into nums. Since the answer may be large, return it modulo 109 + 7

### 解题思路

树状数组，每次插入的指令数相当于吧这个位置的数对应加一，第i个query的结果为`min(sum(a[0]-a[instruction-1]), sum(i - a[instruction]))`

### 代码
```python
class Solution:
    def createSortedArray(self, instructions: List[int]) -> int:
        def update(k):
            while k <= limit:
                range_sum[k] += 1
                k += k & -k
        
        def query(k):
            ret = 0
            while k:
                ret += range_sum[k]
                k -= k & -k
            return ret
        
        limit = max(instructions)
        range_sum = [0] * (limit + 1)
        res = 0
        MOD = 10 ** 9 + 7
        for i, n in enumerate(instructions):
            res += min(query(n - 1), i - query(n)) % MOD
            update(n)
        return res % MOD
```
