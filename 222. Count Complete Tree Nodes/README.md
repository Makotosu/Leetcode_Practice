### 222. Count Complete Tree Nodes

https://leetcode.com/problems/count-complete-tree-nodes/description/

Given the root of a complete binary tree, return the number of the nodes in the tree.

```
Input: root = [1,2,3,4,5,6]
Output: 6
```

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def countNodes(self, root):
        def count_subtree(node):
            if node is None:
                return 0
            return count_subtree(node.left) + count_subtree(node.right) + 1
        
        return count_subtree(root)
```        
