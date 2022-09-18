### 1334. Find the City With the Smallest Number of Neighbors at a Threshold Distance

https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/

There are n cities numbered from 0 to n-1. Given the array edges where edges[i] = [fromi, toi, weighti] represents a bidirectional and weighted edge between cities fromi and toi, and given the integer distanceThreshold.

Return the city with the smallest number of cities that are reachable through some path and whose distance is at most distanceThreshold, If there are multiple such cities, return the city with the greatest number.

Notice that the distance of a path connecting cities i and j is equal to the sum of the edges' weights along that path.

```
Input: n = 4, edges = [[0,1,3],[1,2,1],[1,3,4],[2,3,1]], distanceThreshold = 4
Output: 3
Explanation: The figure above describes the graph. 
The neighboring cities at a distanceThreshold = 4 for each city are:
City 0 -> [City 1, City 2] 
City 1 -> [City 0, City 2, City 3] 
City 2 -> [City 0, City 1, City 3] 
City 3 -> [City 1, City 2] 
Cities 0 and 3 have 2 neighboring cities at a distanceThreshold = 4, but we have to return city 3 since it has the greatest number.
```

```
class Solution:
    def findTheCity(self, n: int, edges: List[List[int]], distanceThreshold: int) -> int:
        
        dp = [[1000000 for x in range(n)] for x in range(n)]
        
        for i in range(n):
            dp[i][i] = 0 
            
        for i in range(len(edges)):
            j,k,l = edges[i][0], edges[i][1],edges[i][2]
            dp[k][j] = l
            dp[j][k] = l 
            
        for k in range(n):
            for i in range(n):
                for j in range(n):
                    if dp[i][j] > dp[i][k] + dp[k][j]:
                        dp[i][j] = dp[i][k] + dp[k][j]
        
        res = []
        
        for i in range(n):
            tmp = sum(x <= distanceThreshold for x in dp[i])
            res.append(tmp - 1)
                    
        indices = [i for i, x in enumerate(res) if x == min(res)]    
        
        return max(indices)
```                    
