### 73. Set Matrix Zeroes

https://leetcode.com/problems/set-matrix-zeroes/

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.

```
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]
```

```
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])
        
        record = []
        
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    record.append((i, j))
        
                    
        for (i, j) in record:
            matrix[i] = [0] * n
            
            for row in range(m):
                matrix[row][j] = 0 
                
        return matrix   # O(mn)
```
