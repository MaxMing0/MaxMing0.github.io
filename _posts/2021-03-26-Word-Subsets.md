---
layout:     post
title:      LeetCode 916 Word Subsetse (Python)
number:     916
level:      Medium
lcurl:      word-subsets
youtube:    rKGoer9YDKk
bilibili1:  //player.bilibili.com/player.html?aid=204758168&bvid=BV1vh411S7r3&cid=315707062&page=1
xigua:      
date:       2021-03-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

We are given two arrays A and B of words.  Each word is a string of lowercase letters.

Now, say that word b is a subset of word a if every letter in b occurs in a, including multiplicity.  For example, "wrr" is a subset of "warrior", but is not a subset of "world".

Now say a word a from A is universal if for every b in B, b is a subset of a. 

Return a list of all universal words in A.  You can return the words in any order.

### 解题思路

将所有B中的所有单词，凑成一个单词，使这个字符串包含b中所有的单词，遍历A中所有单词，只要包含这个单词就可以

### 代码
```python
class Solution:
    def wordSubsets(self, A: List[str], B: List[str]) -> List[str]:
        target = defaultdict(int)
        for word in B:
            for c, v in Counter(word).items():
                target[c] = max(target[c], v)
        res = []
        for word in A:
            ct = Counter(word)
            for c, v in target.items():
                if c not in ct or v > ct[c]:
                    break
            else:
                res.append(word)
        return res
```
