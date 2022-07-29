### 162. Find Peak Element

https://leetcode.com/problems/find-peak-element/

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. 
If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. 
In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

 ```
 Example 1:

Input: nums = [1,2,3,1]
Output: 2
Explanation: 3 is a peak element and your function should return the index number 2.
```

```
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return 0
        
        if len(nums) == 2:
            return nums.index(max(nums))
        
        for i in range(1, len(nums)):
            if i == 1 and nums[0] > nums[i]:
                  return 0 
                
            if len(nums) > i+1:
                if nums[i-1] < nums[i] and nums[i] > nums[i+1]:
                    return i
                
            if i == len(nums)-1:
                if nums[i] > nums[i-1]:
                    return i
```        

