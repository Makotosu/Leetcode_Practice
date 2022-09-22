### 9. Palindrome Number

https://leetcode.com/problems/palindrome-number/

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward.

For example, 121 is a palindrome while 123 is not.

```
Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.

```

```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False 
        
        elif x ==0:
            return True 
        
        else:
            length = 1
            while 10**length<x:
                length += 1
            
            length -= 1 
            
            while x != 0:
                if x//(10 ** length) == x %10:
                    x = x % 10**length // 10
                    length -=2
                else:
                    return False
            return True
```        
