### 780. Reaching Points

https://leetcode.com/problems/reaching-points/

Given four integers sx, sy, tx, and ty, return true if it is possible to convert the point (sx, sy) to the point (tx, ty) through some operations, or false otherwise.

The allowed operation on some point (x, y) is to convert it to either (x, x + y) or (x + y, y).

```
Example 1:

Input: sx = 1, sy = 1, tx = 3, ty = 5
Output: true
Explanation:
One series of moves that transforms the starting point to the target is:
(1, 1) -> (1, 2)
(1, 2) -> (3, 2)
(3, 2) -> (3, 5)
```

```
class Solution:
    def reachingPoints(self, sx: int, sy: int, tx: int, ty: int) -> bool:
        
        if sx > tx or sy > ty:
            return False
        elif sx == tx and sy == ty:
            return True 
        elif sx == tx and (ty-sy)%sx == 0:
            return True 
        elif sy == ty and (tx-sx)%sy == 0:
            return True 
        
        else:
            return self.reachingPoints(sx, sy, tx%ty, ty%tx)
```
