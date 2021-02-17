# Leetcode Easy #1: Two Sum


A humble tutorial for Leetcode challenge #1 Two Sum.

<!--more-->

{{< admonition >}}
This tutorial is based on Python 3. The author had referred several answer from Leetcode community and improvised into this suggested answer.
{{< /admonition >}}


## 1 Problem: Two Sum

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

**You may assume that each input would have exactly one solution, and you may not use the same element twice.**

**You can return the answer in any order.**

**Example**

| Scenario | Input | Target | Output |
| :--- | :--- | :--- | :--- |
| #1 | [ 2,7,11,15 ] | 9 | [ 0,1 ] |
| #2 | [ 3,2,4 ] | 6 | [ 1,2 ] |
| #3 | [ 3,3 ] | 6 | [ 0,1 ] |

---
---
---

## 2 Technical Analysis

### 2.1 Determine every target integer and integers after it in input list

We need to determine every integer in input list and the other integers after the target integer

{{< admonition note "Solution: Using nested for loop" >}}
1. Outer loop: Cycle through the integer in the input list, from first element to the last.
2. Inner loop: Cycle through the integer after the integer from the outer loop

``` python
nums = [1,0,0,2,9]
target = 3

for i in range(len(nums)):
    for j in range(i+1,len(nums)):
        print('Outer loop: {0}, Inner loop: {1}'.format(i,j))
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
Outer loop: 0, Inner loop: 1  
Outer loop: 0, Inner loop: 2  
Outer loop: 0, Inner loop: 3  
Outer loop: 0, Inner loop: 4  
Outer loop: 1, Inner loop: 2  
Outer loop: 1, Inner loop: 3  
Outer loop: 1, Inner loop: 4  
Outer loop: 2, Inner loop: 3  
Outer loop: 2, Inner loop: 4  
Outer loop: 3, Inner loop: 4  
{{< /admonition >}}


### 2.2 Summation of Integer Pair

Integer from outer and inner loop need to be summed and match to the target integer.

{{< admonition note "Solution: Summation of integer pair and check with the target integer" >}}
1. Sum the integer from outer and inner loop.
2. Compare with target integer.
3. Return integer pair indices.

``` python
nums = [1,0,0,2,9]
target = 3

for i in range(len(nums)):
    for j in range(i+1,len(nums)):
        if nums[i] + nums[j] == target:
            print('The integer pair indices: {}'.format([i,j]))
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
The integer pair indices: [0, 3]
{{< /admonition >}}

---
---
---

## 3 Test Bench

``` python
class Solution(object):
    def twoSum(self, nums, target):
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]

nums = [1,0,0,2,9]
target = 3
Solution().twoSum(nums, target)
```

{{< admonition note "Result" >}}
CPU times: user 2 µs, sys: 0 ns, total: 2 µs  
Wall time: 4.77 µs  
[0, 3]  
{{< /admonition >}}
