### 70. Climbing Stairs

https://leetcode.com/problems/climbing-stairs/submissions/

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?


```
Example 2:

Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

```
class Solution:
    def climbStairs(self, n: int) -> int:
        l = [0 for i in range(n+1)]
        l[0] = 1
        l[1] = 1
        for i in range(2,n+1):
            l[i] = l[i-1] + l[i-2]
        return l[-1]
```        
        
        
