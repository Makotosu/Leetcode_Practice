### 532. K-diff Pairs in an Array

https://leetcode.com/problems/k-diff-pairs-in-an-array/

Goldman Sachs | 2021 Goldman Sachs Engineering - Programming | HackerRank OA

Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.

A k-diff pair is an integer pair (nums[i], nums[j]), where the following are true:

0 <= i, j < nums.length
i != j
nums[i] - nums[j] == k
Notice that |val| denotes the absolute value of val.

```
Example 1:

Input: nums = [3,1,4,1,5], k = 2
Output: 2
Explanation: There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of unique pairs.
```

```
class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        output = 0 
        
        if k == 0:
            d = {x:nums.count(x) for x in nums}
            
            for key, value in d.items():
                if value >= 2:
                    output += 1
           
        else:
            nums = sorted(set(nums))

            for i in range(len(nums)):
                if nums[i] + k in nums:
                    output += 1
                
        return output 
```
```
class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        ct = Counter(nums)
        
        res = 0
        if k ==0:
            for v in ct.values():
                res += v > 1
        else:
            for n in ct:
                res += n + k in ct
        return res 
```
