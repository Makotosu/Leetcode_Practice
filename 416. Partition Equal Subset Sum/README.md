### 416. Partition Equal Subset Sum

https://leetcode.com/problems/partition-equal-subset-sum/

Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

```
Example 1:

Input: nums = [1,5,11,5]
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].
```

```
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        
            s = sum(nums)
            nums = sorted(nums)
            
            if s % 2 == 1:
                return False 
            else:
                W = s // 2
                n = len(nums)
                
                K = [[0 for x in range(W+1)] for x in range(n+1)] 
                
                for i in range(n+1):
                    for w in range(W+1):
                        if i ==0 or w ==0:
                            K[i][w] = 0
                        elif nums[i-1] <= w:
                            K[i][w] = max(nums[i-1] + K[i-1][w-nums[i-1]], K[i-1][w])
                        
                        else:
                            K[i][w] = K[i-1][w]
                            
                return True if K[n][W] == W else False
```

```
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        
        if sum(nums) % 2: return False 
        
        st = set([0])
        
        for i in nums:
            for j in list(st):
                st.add(i + j)
                if i + j == sum(nums)//2:
                    return True
        return False
```        
