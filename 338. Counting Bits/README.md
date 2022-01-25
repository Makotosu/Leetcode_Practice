###338. Counting Bits

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

```
Example 1:

Input: n = 2
Output: [0,1,1]
Explanation:
0 --> 0
1 --> 1
2 --> 10
```

```
class Solution:
    def countBits(self, n: int) -> List[int]:      
        l = []
        for i in range(0,n+1):
            target = i            
            res = 0
            while target != 0:
                res += target % 2
                target = target >> 1
       
            l.append(res)
            
        return l 
```
