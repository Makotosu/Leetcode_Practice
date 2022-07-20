### 724. Find Pivot Index

https://leetcode.com/problems/find-pivot-index/

Goldman Sachs | 2021 Goldman Sachs Engineering - Programming | HackerRank OA

Given an array of integers nums, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.

Return the leftmost pivot index. If no such index exists, return -1.

```
Example 1:

Input: nums = [1,7,3,6,5,6]
Output: 3
Explanation:
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
```

```
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        output = []
        ls = 0
        rs = sum(nums[1:])
        
        if ls == rs:
            return 0
        
        else:
        
            for i in range(1, len(nums)):
                ls += nums[i-1]
                rs -= nums[i]
                if ls == rs:
                    output.append(i)
                    break 
                
            return output[0] if len(output) != 0 else -1
```
