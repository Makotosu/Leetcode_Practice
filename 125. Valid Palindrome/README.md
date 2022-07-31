### 125. Valid Palindrome

https://leetcode.com/problems/valid-palindrome/

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

```
Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

```
class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        s = ''.join(ch for ch in s if ch.isalnum())
        
        s = s.lower()
        
        if s == s[::-1]:
            return True 
        else:
            return False 
```
