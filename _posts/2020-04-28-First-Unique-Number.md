---
layout:     post
title:      LeetCode First Unique Number (Python)
number:     9999
level:      na
lcurl:      
youtube:    5IAw4wFV1vs
bilibili1:  //player.bilibili.com/player.html?aid=710496318&bvid=BV1gQ4y1N7tW&cid=184330415&page=1
xigua:      
date:       2020-04-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

ou have a queue of integers, you need to retrieve the first unique integer in the queue.

Implement the FirstUnique class:

- FirstUnique(int[] nums) Initializes the object with the numbers in the queue.
- int showFirstUnique() returns the value of the first unique integer of the queue, and returns -1 if there is no such integer.
- void add(int value) insert value to the queue.

### 解题思路

用所有数建立Counter，从头开始遍历queue，同时维护一个遍历到的位置，如果一个数已经出现过多次，那这个数就再也不会只出现一次

对于add操作，就加入到队列和计数器里

对于showFirstUnique操作，从当前的位置开始遍历，找到第一个出现过第一次的数返回，遍历到队尾还没找到则返回-1

### 代码
```python
from collections import Counter
class FirstUnique:

    def __init__(self, nums: List[int]):
        self.ct = Counter(nums)
        self.cur = 0
        self.nums = nums

    def showFirstUnique(self) -> int:
        while self.cur < len(self.nums):
            if self.ct[self.nums[self.cur]] == 1:
                return self.nums[self.cur]
            self.cur += 1
        return -1

    def add(self, value: int) -> None:
        self.nums.append(value)
        if value not in self.ct:
            self.ct[value] = 1
        else:
            self.ct[value] += 1


# Your FirstUnique object will be instantiated and called as such:
# obj = FirstUnique(nums)
# param_1 = obj.showFirstUnique()
# obj.add(value)
```
