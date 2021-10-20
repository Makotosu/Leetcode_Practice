### 53. Maximum Subarray

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

```
Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

def maxSubArray(self, nums: List[int]) -> int:
        res = [nums[0]]
        max_sub = nums[0]
        for i in nums[1:]:
            j = i if res[-1] < 0 else res[-1] + i
            res.append(j)
            max_sub = max(max_sub,j)
        return max_sub
                
                
