### 540. Single Element in a Sorted Array

https://leetcode.com/problems/single-element-in-a-sorted-array/

# binary search

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return the single element that appears only once.

Your solution must run in O(log n) time and O(1) space.

```
Example 1:

Input: nums = [1,1,2,3,3,4,4,8,8]
Output: 2
```

```
class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
                    
        l, r = -1, len(nums)
        
        while l+1 != r:
            m = (l+r) // 2
            if (m+1 ==r and m-1 == l) or (nums[m-1] != nums[m] and nums[m] != nums[m+1]):
                return nums[m]
            
            elif nums[m+1] == nums[m]:
                if (r-m) % 2 ==0:
                    r = m
                else:
                    l = m+1
            elif nums[m-1] == nums[m]:
                if (m-l)%2 == 0:
                    l = m
                else:
                    r = m-1
```        

```
def binarySearch(array, x, low, high):

    # Repeat until the pointers low and high meet each other
    while low <= high:

        mid = low + (high - low)//2

        if array[mid] == x:
            return mid

        elif array[mid] < x:
            low = mid + 1

        else:
            high = mid - 1

    return -1
```
