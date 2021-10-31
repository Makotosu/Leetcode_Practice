### Minimum Absolute Difference in an Array
Given an array of integers, find the minimum absolute difference between any two elements in the array.
```
ample Input 0
3
3 -7 0
Sample Output 0
3
```

Brute Force
```
def minimumAbsoluteDifference(arr):
    # Write your code here
    res = []
    for i in range(len(arr)-1):
        for j in range(i + 1,len(arr)):
            res.append(abs(arr[i] - arr[j]))
    return min(res)
```

Sorted List
```
def minimumAbsoluteDifference(arr):
    # Write your code here
    l = sorted(list(arr))
    diff = []
    for i in range(1, len(l)):
        diff.append(l[i] - l[i-1])
    return min(diff)
```
