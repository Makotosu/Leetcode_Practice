### 204. Count Primes

https://leetcode.com/problems/count-primes/

Given an integer n, return the number of prime numbers that are strictly less than n.

```
Example 1:
Input: n = 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```

```
class Solution:
    def countPrimes(self, n: int) -> int:
        
        lst = [i for i in range(n)]
        
        def isprime(num):
            if num> 1:  
                for n in range(2,num):  
                    if (num % n) == 0:  
                        return False
                return True
            else:
                return False
                   
        count = 0
        for i in range(len(lst)):
            if isprime(lst[i]) == True:
                count += 1
                
        return count
```

