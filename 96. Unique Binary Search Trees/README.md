### 96. Unique Binary Search Trees

https://leetcode.com/problems/unique-binary-search-trees/description/

Given an integer n, return the number of structurally unique BST's (binary search trees) which has exactly n nodes of unique values from 1 to n.

```
Input: n = 3
Output: 5
```

```
class Solution:
    def numTrees(self, n: int) -> int:

        # numTree[4] = numTree[3]*numTree[0] +                     
                       numTree[2] * numTree[1] +                      
                       numTree[1] * numTree[2] +                      
                       numTree[0] * numTree[3]

        dp = [0] * (n+1) 
        dp[0], dp[1] = 1, 1

        for i in range(2, n+1):
            total = 0 
            for j in range(1, i+1):
                left = j-1 
                right = i - j
                total += dp[left] * dp[right]
            dp[i] = total 

        return dp[n] 
```        
