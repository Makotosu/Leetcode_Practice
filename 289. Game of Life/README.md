### 289. Game of Life

https://leetcode.com/problems/game-of-life/

The board is made up of an m x n grid of cells, where each cell has an initial state: live (represented by a 1) or dead (represented by a 0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules (taken from the above Wikipedia article):

Any live cell with fewer than two live neighbors dies as if caused by under-population.
Any live cell with two or three live neighbors lives on to the next generation.
Any live cell with more than three live neighbors dies, as if by over-population.
Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.


```
Example 1
Input: board = [[0,1,0],[0,0,1],[1,1,1],[0,0,0]]
Output: [[0,0,0],[1,0,1],[0,1,1],[0,1,0]]
```

```
class Solution:
    def gameOfLife(self, board: List[List[int]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """

        neighbors = [(1,0), (1,-1), (0,-1), (-1,-1), (-1,0), (-1,1), (0,1), (1,1)]

        rows = len(board)
        cols = len(board[0])

        for row in range(rows):
            for col in range(cols):

                live_neighbors = 0
                for neighbor in neighbors:

                    r = (row + neighbor[0])
                    c = (col + neighbor[1])

                    if (r < rows and r >= 0) and (c < cols and c >= 0) and abs(board[r][c]) == 1:
                        live_neighbors += 1

                if board[row][col] == 1 and (live_neighbors < 2 or live_neighbors > 3):

                    board[row][col] = -1

                if board[row][col] == 0 and live_neighbors == 3:

                    board[row][col] = 2

        for row in range(rows):
            for col in range(cols):
                if board[row][col] > 0:
                    board[row][col] = 1
                else:
                    board[row][col] = 0
```                    

```
class Solution:
    def gameOfLife(self, board: List[List[int]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """

        neighbors = [(1,0), (1,-1), (0,-1), (-1,-1), (-1,0), (-1,1), (0,1), (1,1)]

        rows = len(board)
        cols = len(board[0])

        ref = [[0 for x in range(cols)] for x in range(rows)]
        
        for i in range(rows):
            for j in range(cols):
                live_neighbors = 0
                
                for x in neighbors:
                    r = i + x[0]
                    c = j + x[1] 
                    
                    if (r < rows and r>=0) and (c < cols and c>=0) and board[r][c] ==1:
                        live_neighbors += 1
                ref[i][j] = live_neighbors  
                
        for i in range(rows):
            for j in range(cols):
                if (board[i][j] == 1) and (ref[i][j] < 2):
                    board[i][j] = 0 
                elif (board[i][j] ==1) and (ref[i][j] == 2 or ref[i][j]==3):
                    board[i][j] =1
                elif (board[i][j] ==1) and (ref[i][j] > 3):
                    board[i][j] = 0
                elif (board[i][j] ==0) and (ref[i][j] ==3):
                    board[i][j] = 1
                else:
                    continue 
                    
        return board 
```        
