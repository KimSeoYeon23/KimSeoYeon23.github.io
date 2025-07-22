---
layout: post
title:  "LeetCode Plus One"
date:   2025-07-21 16:04:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
  {:toc}



## LeetCode Plus One

### 문제

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

### 입출력 예

Example 1:

Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
Incrementing by one gives 123 + 1 = 124.
Thus, the result should be [1,2,4].
Example 2:

Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
Incrementing by one gives 4321 + 1 = 4322.
Thus, the result should be [4,3,2,2].
Example 3:

Input: digits = [9]
Output: [1,0]
Explanation: The array represents the integer 9.
Incrementing by one gives 9 + 1 = 10.
Thus, the result should be [1,0].


### 풀이

```py
class Solution:
  def plusOne(self, digits: List[int]) -> List[int]:
    convert_str = list(map(str, digits))
    convert_int = ''.join(convert_str)
    sum_num = int(convert_int) + 1
    result = list(map(int, str(sum_num)))

    return result
```
