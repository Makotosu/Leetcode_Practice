### 47. Permutations II

https://leetcode.com/problems/permutations-ii/description/

Given a collection of numbers, nums, that might contain duplicates, return all possible unique permutations in any order.
```
Example 1:

Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

```
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:

        res = [] 
        perm = []

        count = {n:0 for n in nums}
        for n in nums:
            count[n] += 1

        def dfs():
            if len(perm) == len(nums):
                res.append(perm.copy())
                return 

            for n in count:
                if count[n] > 0:
                    perm.append(n)
                    count[n] -= 1

                    dfs()
                    
                    # clean up 
                    count[n] += 1
                    perm.pop() 
        
        dfs()
        return res 
```        
