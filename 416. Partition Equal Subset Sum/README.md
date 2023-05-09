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
        total_sum = sum(nums)
        
        if total_sum % 2 != 0:
            return False
        
        target_sum = total_sum // 2
        dp = [False] * (target_sum + 1)
        dp[0] = True
        # dp where dp[i] represents whether it is possible to form a sum of i using the given numbers in the array.

        for num in nums:
            for i in range(target_sum, num-1, -1):
                dp[i] = dp[i] or dp[i-num]
                
                # This means that we can form a sum of i using either the previous elements we have already processed or by adding the current num to the sum of i-num that we have already computed. We iterate over i in reverse order to ensure that we only consider sums that are smaller than or equal to the target sum.
        return dp[target_sum]
```        
