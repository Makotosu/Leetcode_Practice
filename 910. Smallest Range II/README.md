### 910. Smallest Range II

https://leetcode.com/problems/smallest-range-ii/

You are given an integer array nums and an integer k.

For each index i where 0 <= i < nums.length, change nums[i] to be either nums[i] + k or nums[i] - k.

The score of nums is the difference between the maximum and minimum elements in nums.

Return the minimum score of nums after changing the values at each index.

```
Example 1:

Input: nums = [1,3,6], k = 3
Output: 3
Explanation: Change nums to be [4, 6, 3]. The score is max(nums) - min(nums) = 6 - 3 = 3.
```

```
class Solution:
    def smallestRangeII(self, nums: List[int], k: int) -> int:

        nums = sorted(nums)
        mn, mx = nums[0], nums[-1]
        res = mx - mn
    
        for i in range(len(nums)-1):
            mx = max(nums[-1] - k, nums[i]   + k)
            mn = min(nums[0]  + k, nums[i+1] - k)
            res = min(res, mx - mn)

        return res
```
