---
layout:     post
title:      LeetCode 1570 Dot Product of Two Sparse Vectors (Python)
number:     1570
level:      Medium
lcurl:      dot-product-of-two-sparse-vectors
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
---

### 题目

Given two sparse vectors, compute their dot product.

Implement class SparseVector:

- SparseVector(nums) Initializes the object with the vector nums
- dotProduct(vec) Compute the dot product between the instance of SparseVector and vec
A sparse vector is a vector that has mostly zero values, you should store the sparse vector efficiently and compute the dot product between two SparseVector.

Follow up: What if only one of the vectors is sparse?

### 解题思路

方法一，直接按照向量相乘计算结果

方法二，在构造函数中，用字典记录不是0的位置以及对应的数，在做相乘的时候，只判断这些位置是否在另外的向量中不为0，再进行相乘

### 代码
```python
class SparseVector:
    def __init__(self, nums: List[int]):
        self.nums = nums

    # Return the dotProduct of two sparse vectors
    def dotProduct(self, vec: 'SparseVector') -> int:
        res = 0
        for i in range(len(vec.nums)):
            if self.nums[i] != 0 and vec.nums[i] != 0:
                res += self.nums[i] * vec.nums[i]
        return res

# Your SparseVector object will be instantiated and called as such:
# v1 = SparseVector(nums1)
# v2 = SparseVector(nums2)
# ans = v1.dotProduct(v2)
```
```python
class SparseVector:
    def __init__(self, nums: List[int]):
        self.dic = {}
        for i, n in enumerate(nums):
            if n != 0:
                self.dic[i] = n

    # Return the dotProduct of two sparse vectors
    def dotProduct(self, vec: 'SparseVector') -> int:
        res = 0
        for i, n in self.dic.items():
            if i in vec.dic:
                res += n * vec.dic[i]
        return res
```
