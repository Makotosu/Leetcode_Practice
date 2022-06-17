### 435. Non-overlapping Intervals

https://leetcode.com/problems/non-overlapping-intervals/

Given an array of intervals intervals where intervals[i] = [starti, endi], 
return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

Example 1:

Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
Output: 1
Explanation: [1,3] can be removed and the rest of the intervals are non-overlapping.


```
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        
        intervals.sort(key = lambda x:x[1])
        
        prev_end, count = float('-inf'), 0 
        
        for start, end in intervals:
            if start >= prev_end:
                count += 1
                prev_end = end      #calculate number of non-overlapping intervals first
                
        return len(intervals) - count 
```
