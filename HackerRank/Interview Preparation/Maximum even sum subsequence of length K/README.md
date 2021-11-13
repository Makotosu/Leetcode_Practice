Maximum even sum subsequence of length K

Given an array arr[] consisting of N positive integers, and an integer K, the task is to find the maximum possible even sum of any subsequence of size K. If it is not possible to find any even sum subsequence of size K, then print -1.
```
Input: arr[] ={4, 2, 6, 7, 8}, K = 3
Output: 18
Explanation: Subsequence having maximum even sum of size K( = 3 ) is {4, 6, 8}.
Therefore, the required output is 4 + 6 + 8 = 18.

```
```
def get_max_even_sum (input_arr, k):
    if k > len(input_arr) or len(input_arr) == 0:
        return -1

    even_arr = []
    odd_arr = []
    # sort the arr
    input_arr.sort(reverse = True)
    
    # separate out the even and odd arr
    for i in range(len(input_arr)):
        if input_arr[i]%2 == 0:
            even_arr.append(input_arr[i])
        else:
            odd_arr.append(input_arr[i])
    
    # take the max and keep track of the remaining
    even_index, odd_index = 0, 0
    max_sum = 0
    
    # Go Greedy
    # think about the case with only 1 or 2 element
    # for 1:
        # we must take the highest from the even Array
        # for 2: we can either take (even + even = even) or (odd + odd = even) 
            # since even + odd is not equal to even
            # we take max(current + next number) from even and odd array

    while k > 0:
        if k % 2 == 1:
            if (len(even_arr) > 0):
                max_sum += even_arr[even_index]
                even_index += 1
                k -= 1
            else:
                return -1
        else:
            if even_index < len(even_arr) - 1 and odd_index < len(odd_arr) - 1:
                max_sum += max(even_arr[even_index] + even_arr[even_index + 1], odd_arr[odd_index] + odd_arr[odd_index + 1])
                even_index += 2
                odd_index += 2
            elif even_index < len(even_arr) - 1:
                max_sum += even_arr[even_index] + even_arr[even_index + 1]
                even_index += 2
            elif odd_index < len(odd_arr) - 1:
                max_sum += odd_arr[odd_index] + odd_arr[odd_index + 1]
                odd_index += 2
            
            k -= 2

    return max_sum        
```
