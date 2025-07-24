---
layout: post
title:  "Two Sum"
date:   2025-07-18 11:48:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## LeetCode Two Sum

### 문제

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.


### 예시

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]


### 풀이

```py
class Solution:
  def twoSum(self, nums: List[int], target: int) -> List[int]:
    prevMap = {}

    for i, num in enumerate(nums):
      diff = target - num
      if diff in prevMap:
        return [prevMap[diff], i]
      prevMap[num] = i       
```
