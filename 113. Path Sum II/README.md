### 113. Path Sum II

https://leetcode.com/problems/path-sum-ii/

Given the root of a binary tree and an integer targetSum, return all root-to-leaf paths where the sum of the node values in the path equals targetSum. Each path should be returned as a list of the node values, not node references.

A root-to-leaf path is a path starting from the root and ending at any leaf node. A leaf is a node with no children.


```
Example1 
Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: [[5,4,11,2],[5,8,4,5]]
Explanation: There are two paths whose sum equals targetSum:
5 + 4 + 11 + 2 = 22
5 + 8 + 4 + 5 = 22
```

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        if not root:
            return []
        # dfs function to find path from root to leaf
        def dfs(root,path):
            # to check if node is leaf
            if not root.left and not root.right:
                # if leaf then check if path sum matches target sum
                if targetSum==sum(path+[root.val]):
                    # if yes then add path to result array
                    return res.append(path+[root.val])
            # recursively cal for left and right nodes till leaf node
            if root.left is not None:
                dfs(root.left,path+[root.val])
            if root.right is not None:
                dfs(root.right,path+[root.val])
        # create a result array
        res=[]
        # call the function for root
        dfs(root,[])
        return res
```        
