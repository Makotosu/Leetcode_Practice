### 238. Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

```
Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        l = len(nums)
        output = []
        
        for i in range(l):
            temp = nums.copy()
            temp.remove(nums[i])
            result = 1
            for x in temp:
                result = x*result
            output.append(result)
        return output 
```
```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        # use a prefix and postfix 
        l = len(nums)
        pre = [None] * l
        post = [None] * l
        pre[0] = nums[0]
        post[l-1] = nums[l-1]
        for i in range(1,l):
            pre[i] = pre[i-1]*nums[i]
            post[l-1-i] = post[l-i]*nums[l-1-i]
        
        output = []
        output.append(1*post[1])
        for i in range(1,l-1):
            output.append(pre[i-1]*post[i+1])
        output.append(pre[l-2]*1)
        
        return output
  ```
  
 model solution 
 ```
 class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1]*len(nums)
        
        prefix = 1
        for i in range(len(nums)):
            res[i] = prefix 
            prefix *= nums[i]
        postfix = 1
        for i in range(len(nums) -1,-1,-1):
            res[i]*= postfix 
            postfix *= nums[i] 
        return res 
  ```
  
