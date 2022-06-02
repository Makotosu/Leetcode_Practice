### 62. Unique Paths

https://leetcode.com/problems/unique-paths/

There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). 
The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). 
The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.

Example 1:

Input: m = 3, n = 2
Output: 3

```
class Solution(object):
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        buckets = [[0 for col in range(n)] for row in range(m)]
        
        buckets[0] = [1 for col in range(n)]
        
        for row in range(m):
            buckets[row][0] = 1
        
        for i in range(1, m):
            for j in range(1, n):
                buckets[i][j] = buckets[i][j-1] + buckets[i-1][j]
        
        return buckets[-1][-1] 
```
