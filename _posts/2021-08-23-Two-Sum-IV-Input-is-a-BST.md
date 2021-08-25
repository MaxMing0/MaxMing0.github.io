---
layout:     post
title:      LeetCode 653 Two Sum IV - Input is a BST (Python)
number:     635
level:      Easy
lcurl:      two-sum-iv-input-is-a-bst
youtube:    JMBhKN1M64w
bilibili1:  //player.bilibili.com/player.html?aid=717532642&bvid=BV1AQ4y117mc&cid=396224807&page=1
xigua:      
date:       2021-08-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

Given the root of a Binary Search Tree and a target number k, return true if there exist two elements in the BST such that their sum is equal to the given target.

### 解题思路

遍历这个树，并把遇到的数加到一个集合里，如果target-新遇到的数存在在集合里，则返回True

### 代码
```python
class Solution:
    def findTarget(self, root: Optional[TreeNode], k: int) -> bool:
        nums = set()
        s = [root]
        while s:
            cur = s.pop()
            if k - cur.val in nums:
                return True
            nums.add(cur.val)
            if cur.left:
                s.append(cur.left)
            if cur.right:
                s.append(cur.right)
        return False
```
