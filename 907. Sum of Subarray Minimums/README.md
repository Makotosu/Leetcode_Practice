### 907. Sum of Subarray Minimums

https://leetcode.com/problems/sum-of-subarray-minimums/description/

Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. 
Since the answer may be large, return the answer modulo 109 + 7.

```
Example 1:

Input: arr = [3,1,2,4]
Output: 17
Explanation: 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17.
```

```
# brute force 
class Solution:
    def sumSubarrayMins(self, arr: List[int]) -> int:

        all = [arr[i:i+j] for i in range(0,len(arr)) for j in range(1,len(arr)-i+1)]
        res = 0
        for x in all:
            res += min(x)

        return res
```

```
class Solution:
    def sumSubarrayMins(self, A: List[int]) -> int:
        n = len(A)
        next_smaller = [n] * n
        prev_smaller = [0] * n
        
        ns_s = []
        ps_s = []
        for i, a in enumerate(A):
            while ns_s and A[ns_s[-1]] > a:
                j = ns_s.pop()
                next_smaller[j] = i
            
            ns_s.append(i)
                
            while ps_s and A[ps_s[-1]] > a:
                ps_s.pop()
                
            if ps_s:
                prev_smaller[i] = ps_s[-1]
            else:
                prev_smaller[i] = -1
                
            ps_s.append(i)
        
        res = 0
        for i, a in enumerate(A):
            res += (i - prev_smaller[i]) * a * (next_smaller[i] - i)
            
        return res % (10**9 + 7)
```
