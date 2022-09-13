### 213. House Robber II

https://leetcode.com/problems/house-robber/submissions/

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

```
Example 1:

Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

```
class Solution:
    def rob(self, nums: List[int]) -> int:
        
        if len(nums) == 1:
            return nums[0]
        elif len(nums) == 2:
            return max(nums)
        else:
            rob = []
            rob.append(nums[0])
            rob.append(max(nums[0:2]))
            
            for i in range(2, len(nums)):
                tmp = max(rob[i-1], rob[i-2] + nums[i])
                rob.append(tmp)
            return rob[-1]
```        
