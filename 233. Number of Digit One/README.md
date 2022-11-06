### 233. Number of Digit One

https://leetcode.com/problems/number-of-digit-one/description/

Given an integer n, count the total number of digit 1 appearing in all non-negative integers less than or equal to n.

```
Example 1:

Input: n = 13
Output: 6
```

```
class Solution:
    def countDigitOne(self, n: int) -> int:
        if n == 0: return 0
        res,m = 0,1

        while m <= n:
            a, b = n // m, n % m
            if a%10 > 1: res += (a//10 + 1) * m
            elif a%10 == 1: res += (a//10)*m + b + 1
            elif a%10 == 0: res += (a//10)*m
            m *= 10

        return res    
```        
