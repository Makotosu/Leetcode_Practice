### 1283. Find the Smallest Divisor Given a Threshold

https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/

Given an array of integers nums and an integer threshold, we will choose a positive integer divisor, divide all the array by it, and sum the division's result. Find the smallest divisor such that the result mentioned above is less than or equal to threshold.

Each result of the division is rounded to the nearest integer greater than or equal to that element. (For example: 7/3 = 3 and 10/2 = 5).

The test cases are generated so that there will be an answer.

```
Example 1:

Input: nums = [1,2,5,9], threshold = 6
Output: 5
Explanation: We can get a sum to 17 (1+2+5+9) if the divisor is 1. 
If the divisor is 4 we can get a sum of 7 (1+1+2+3) and if the divisor is 5 the sum will be 5 (1+1+1+2). 
```

```
class Solution:
    def smallestDivisor(self, nums: List[int], threshold: int) -> int:
    
        for i in range(1, max(nums)+1):
            new_list = [int(x/i) + (not (x/i).is_integer()) for x in nums] 
            if sum(new_list) <= threshold:
                res = i 
                break 
            else:
                continue 
        return res  
        # Runtime error 
```

```
class Solution:

    def isValid(self, val, nums, threshold):        
        sum = 0
        # Get the sum
        for num in nums: sum += ceil(num/val)
        # It is a valid value if the sum of less than or equal to threshold
        return sum <= threshold

    
    def smallestDivisor(self, nums: List[int], threshold: int) -> int:
        # Binary Search on Answer
        
        # We are asked for the smallest divisor
        # What can be the range of possible divisors?
        
        
        # It can be at least 1
        
        # If we take any number that is greater than any value in list
        # Then we will always get the same result
        # So it makes sense to choose the upper limit of the divisor as the maximum value in the list
        
        start = 1
        end = max(nums)
        
        # Result is the divisor we want to return
        # We want to minimize this result 
        # i.e., smallest possible divisor that satisfies the condition
        result = -1
        
        while start <= end:
            mid = start + (end - start) // 2
            
            # Check if "mid" value as divisor satisfies the conndition
            # If yes, that means, all values bigger than it will also satisfy
            if self.isValid(mid, nums, threshold):
                # So it is one possible solution
                result = mid
                # Since we want to minimize the divisor
                # we keep searching on left of mid
                end = mid - 1
            # If "mid" value as divisor does not satisfy the condition
            # no value less than mid will satisfy
            # So search for a valid value on right side of mid
            else: 
                start = mid + 1
                
        return result
```

