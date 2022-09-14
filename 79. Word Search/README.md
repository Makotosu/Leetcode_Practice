### 79. Word Search

https://leetcode.com/problems/word-search/

Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. 
The same letter cell may not be used more than once.

```
Example
Input: board = [["A","B","C","E"],
                ["S","F","C","S"],
                ["A","D","E","E"]], 
                
                word = "ABCCED"
Output: true
```

```
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        m, n = len(board), len(board[0])
        
        def find(i, j, pos = 0):
            if pos == len(word):
                return True
            if not(0 <= i < m) or not(0 <= j < n) or board[i][j] == "#":
                return False
            if board[i][j] == word[pos]:
                temp = board[i][j]
                board[i][j] = "#"
                if find(i, j-1, pos+1) or find(i, j+1, pos+1) or find(i-1, j, pos+1) or find(i+1, j, pos+1):
                    return True
                board[i][j] = temp
            
            return False
        
        for i in range(m):
            for j in range(n):
                if find(i ,j):
                    return True
        return False
```        

```
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        
        Row = len(board)
        Col = len(board[0])
        path = set()
        
        def dfs(r, c, i):
            if i == len(word):
                return True 
            if (r<0 or c<0 or 
               r >= Row or c >= Col or 
               word[i] != board[r][c] or 
               (r, c) in path):
                return False 
            
            path.add((r, c))
            res = (dfs(r+1, c, i+1) or 
                  dfs(r, c+1, i+1) or 
                  dfs(r-1, c, i+1) or 
                  dfs(r, c-1, i+1))
            path.remove((r, c))
            return res 
        
        for r in range(Row):
            for c in range(Col):
                if dfs(r, c, 0): return True 
        return False 
```        
