### 101. Symmetric Tree

https://leetcode.com/problems/symmetric-tree/ 

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

```
Example 
Input: root = [1,2,2,3,4,4,3]
Output: true
```

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def check(l, r):
            if not l and not r:
                return True
            if l is None or r is None:
                return False
            if l.val != r.val:
                return False 
            return check(l.left, r.right) and check(l.right, r.left)
        
        return check(root.left, root.right)        

```

