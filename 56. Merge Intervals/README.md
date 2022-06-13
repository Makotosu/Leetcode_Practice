### 56. Merge Intervals
https://leetcode.com/problems/merge-intervals/

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

```
Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```
```
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        fill = []
        for [i,j] in intervals:
            line = [k for k in range(i,j+1)]
            fill.extend(line)
        
        l = set(fill)
        l2 = set([i for i in range(min(l),max(l)+1)])
        diff = list(l2 - l)
        
        output = []
        output.append([min(l), min(diff) - 1])
        for i in range(1,len(diff)):
            if diff[i] - diff[i-1] >1:
                output.append([diff[i-1]+1, diff[i]-1])
             
        
        output.append([max(diff)+1, max(l)])
        
        return output 
```
```
class Solution(object):
    def merge(self, intervals):
        # O(nlogn)
        intervals.sort(key = lambda i :i[0])
        output = [intervals[0]]
        
        for i,j in intervals[1:]:
            lastEnd = output[-1][1]
            
            if i <= lastEnd: # Overlap
                output[-1][1] = max(lastEnd, j)
            else: 
                output.append([i,j])
                
            # [1,5], [2,4] = [1,5]
            # [1,5], [7,8] = [1,5], [7,8]
            
        return output
```        
