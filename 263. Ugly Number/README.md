263. Ugly Number

https://leetcode.com/problems/ugly-number/description/

An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.

Given an integer n, return true if n is an ugly number.

```
Example 1:

Input: n = 6
Output: true
Explanation: 6 = 2 × 3
```

```
class Solution:
    def isUgly(self, n: int) -> bool:
        if n == 1:
            return True 

        elif n < 1:
            return False 
        
        while (n%2 == 0) or (n%3==0) or (n%5 ==0):
            l = [2, 3, 5]
            for i in l:
                if n%i == 0:
                    n = n/i 
        return n == 1
```        
