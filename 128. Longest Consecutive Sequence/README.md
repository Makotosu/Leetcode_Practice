### 128. Longest Consecutive Sequence

https://leetcode.com/problems/longest-consecutive-sequence/submissions/

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

```
Example 1:

Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

```
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        
        if nums == []:
            return 0
        
        else:
            nums = sorted(set(nums))
        
            res = 1
            output = [1]
        
            for i in range(1, len(nums)):
                if nums[i] == nums[i-1] + 1:
                    res += 1
                else:
                    output.append(res)
                    res = 1 
                
            output.append(res) 
            return max(output)
```
