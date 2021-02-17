# Leetcode Easy #7: Reverse Integer


A humble tutorial for Leetcode challenge #7 Reverse Integer.

<!--more-->

{{< admonition >}}
This tutorial is based on Python 3. The author had referred several answer from Leetcode community and improvised into this suggested answer.
{{< /admonition >}}


## 1 Problem: Reverse Integer

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range $ -2^{31} \le y \le 2^{31} - 1 $, then return 0.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned)**

**Example**

| Scenario | Input | Output |
| --- | --- | --- |
| #1 | 123 | 321 |
| #2 | -123 | -321 |
| #3 | 120 | 21 |
| #4 | 0 | 0 |

---
---
---

## 2 Technical Analysis

### 2.1 Integer Sign

We need to determine the input interger sign and expect the output with the same sign.

{{< admonition note "Solution: Determine sign of interger by math logic" >}}
1. First determine the integer sign by comparing input to 0 (zero). Expected output is a Boolean type.
2. Then use Boolean type data as integer, *True == 1* & *False == 0*, to identify the sign

``` python
x = -203

s = (x > 0) - (x < 0)
print('The sign of input is {}'.format(s))
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
The sign of input is -1
{{< /admonition >}}


### 2.2 Reverse Integer

Numbers in the integer need to be reversed.

{{< admonition note "Solution: Convert integer to string type and reverse using slicing" >}}
1. Convert input integer to sign-less integer.
2. Cast sign-less input to string type.
3. Use slice string to reverse. Slice rule [ start : end : step ].
4. Cast string type reversed sign-less data back to integer.

``` python
x = -203

s = (x > 0) - (x < 0)
r = int(str(x*s)[::-1])
print('The reversed input is {}'.format(r))
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
The reversed input is 302
{{< /admonition >}}

### 2.3 Contraint

The challenge's contraint is the reversed integer value must be within the range of 
$$ -2^{31} \le y \le 2^{31} - 1 $$

{{< admonition note "Solution: Multiply signed reversed integer with boolean value" >}}
1. State the constraint above.
2. Multiply boolean result of the contraint to *sign* and *reversed integer*.

``` python
x = -203

s = (x > 0) - (x < 0)
r = int(str(x*s)[::-1])
c = (r >= (-(2**31))) and (r <= ((2**31)-1))
z = s * r * c
print('The reverse intger is {}'.format(z))
```
{{< /admonition >}}

{{< admonition note "Expected Output" >}}
The reverse intger is -302
{{< /admonition >}}

---
---
---

## 3 Test Bench

``` python
class Solution(object):
    def reverse(self, x):
        s = (x > 0) - (x < 0)
        r = int(str(x*s)[::-1])
        c = (r >= (-(2**31))) and (r <= ((2**31)-1))
        y = s*r*c
        return y

input = -203
Solution().reverse(input)
```

{{< admonition note "Result" >}}
CPU times: user 2 µs, sys: 1 µs, total: 3 µs  
Wall time: 4.77 µs  
-302  
{{< /admonition >}}
