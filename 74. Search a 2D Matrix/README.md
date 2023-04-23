### 74. Search a 2D Matrix

https://leetcode.com/problems/search-a-2d-matrix/description/

You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

```
Example 1

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

```
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        index = [x[0] for x in matrix]

        low, high = -1, len(index)

        while low+1 < high: 
            mid = (low + high) // 2 

            if index[mid] == target: 
                row = mid
                break  
            elif index[mid] < target: 
                low = mid 
                row = low
            else:
                high = mid 
                row = low

        low, high = -1, len(matrix[0])

        while low + 1 < high:
            mid = (low + high) // 2

            if matrix[row][mid] == target:
                return True
                break 

            elif matrix[row][mid] < target:
                low = mid 

            else: 
                high = mid

        return False 
```

```
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
                # Binary Search
        row, col = len(matrix), len(matrix[0])
        i, j = -1, row*col 

        while i+1 != j:
            mid = (i + j) // 2
            mid_element = matrix[mid // col][mid % col]

            if mid_element == target:
                return True
            elif mid_element < target:
                i = mid 
            else:
                j = mid
        return False
```        
