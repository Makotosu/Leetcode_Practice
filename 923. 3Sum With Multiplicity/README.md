### 923. 3Sum With Multiplicity

https://leetcode.com/problems/3sum-with-multiplicity/

Given an integer array arr, and an integer target, return the number of tuples i, j, k such that i < j < k and arr[i] + arr[j] + arr[k] == target.

As the answer can be very large, return it modulo 109 + 7.

```
Example 1:

Input: arr = [1,1,2,2,3,3,4,4,5,5], target = 8
Output: 20
Explanation: 
Enumerating by the values (arr[i], arr[j], arr[k]):
(1, 2, 5) occurs 8 times;
(1, 3, 4) occurs 8 times;
(2, 2, 4) occurs 2 times;
(2, 3, 3) occurs 2 times.
```

```
class Solution:
    def threeSumMulti(self, arr: List[int], target: int) -> int:
        
        c = Counter(arr) 
        output = 0 
        
        for i in c:
            for j in c:
                if j >= i:
                    k = target - i - j
                    if k >= i and k >= j and k in c:
                        if i == j == k:
                            output += c[i] * (c[i]-1) * (c[i]-2) / 6
                        elif i == j != k:
                            output += c[i] * (c[i]-1) * c[k] / 2
                        elif i != j == k:
                            output += c[i] * c[j] * (c[j] -1) / 2
                        else:
                            output += c[i] * c[j] * c[k] 
                    
        return int(output) % (10**9 + 7)
```       
