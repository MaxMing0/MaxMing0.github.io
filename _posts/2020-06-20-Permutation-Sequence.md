---
layout:     post
title:      LeetCode 60 Permutation Sequence (Python)
number:     60
level:      Medium
lcurl:      permutation-sequence
youtube:    yjBve27QSWQ
bilibili1:  //player.bilibili.com/player.html?aid=668517207&bvid=BV1Ma4y1Y7rG&cid=203913409&page=1
xigua:      
date:       2020-06-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

The set `[1,2,3,...,n]` contains a total of `n!` unique permutations.

By listing and labeling all of the permutations in order, we get the following sequence for n = 3:

1. "123"
2. "132"
3. "213"
4. "231"
5. "312"
6. "321"
Given n and k, return the kth permutation sequence.

##### Note:

1. Given n will be between 1 and 9 inclusive.
2. Given k will be between 1 and n! inclusive.

### 解题思路

以n=5，k=67为例子，第67个排列的第一位是 67 / (4!) 上取整为3，第三个数是3，并把3去掉

第二位是 (67-2*(4!)) / (3!) 上取整为4，第四个数是5，并把5去掉，以此类推

### 代码
```python
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        f, nums = [1], [0]
        for i in range(1, n + 1):
            f.append(f[i - 1] * i)
            nums.append(i)
        res = []
        for i in range(n - 1, -1, -1):
            idx = math.ceil(k / f[i])
            res.append(nums.pop(idx))
            k -= (idx - 1) * f[i]
        return ''.join(map(str, res))
```
