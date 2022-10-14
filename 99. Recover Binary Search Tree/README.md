### 99. Recover Binary Search Tree

https://leetcode.com/problems/recover-binary-search-tree/

You are given the root of a binary search tree (BST), where the values of exactly two nodes of the tree were swapped by mistake. 
Recover the tree without changing its structure.

```
Example 1
Input: root = [1,3,null,null,2]
Output: [3,1,null,null,2]
Explanation: 3 cannot be a left child of 1 because 3 > 1. Swapping 1 and 3 makes the BST valid.
```

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def recoverTree(self, root):
	
    # the idea is the in order BST is always increasing, if not, then there is something wrong
        def inorderBST(root):
            if not root: return
            
            # track left side to start with min
            inorderBST(root.left)

            # so that the first prev is the smallest node
            # and update each time
            if self.prev:
                # when order is wrong
				# check the examples in the illustration
                if self.prev.val > root.val:
                    if not self.first:
                        self.first = self.prev
                    self.second = root
            
            # update the prev node
            self.prev = root
            
            # check right side
            inorderBST(root.right)
        
        
        self.first = self.second = self.prev = None
        inorderBST(root)
        
        # swap the two wrong ones
        self.first.val, self.second.val = self.second.val, self.first.val
        return
```
