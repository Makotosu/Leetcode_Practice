### 152. Maximum Product Subarray

Given an integer array nums, find a contiguous non-empty subarray within the array that has the largest product, and return the product.

It is guaranteed that the answer will fit in a 32-bit integer.

A subarray is a contiguous subsequence of the array.

```
Example 1:

Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```

Brute Force
```
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        
        output = []
        for i in range(len(nums)):
            product = 1
            for j in range(i,len(nums)):
                product = product*nums[j]
                output.append(product)
        return max(output)
```

Better Solution 
```
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        res = max(nums) 
        curMin, curMax = 1,1 
        
        for n in nums:
            if n == 0:
                curMin, curMax = 1,1
                continue 
            
            tmp = curMax * n
            curMax = max(n*curMax, n*curMin, n) #[-1,8]
            curMin = min(tmp, n*curMin, n) #[-1,-8]
            
            res = max(res, curMax)
        return res
 ```       
