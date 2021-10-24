### Minimum Swaps 2

You are given an unordered array consisting of consecutive integers  [1, 2, 3, ..., n] without any duplicates. You are allowed to swap any two elements. Find the minimum number of swaps required to sort the array in ascending order.

```
Sample Input 1
5
2 3 4 1 5
Sample Output 1
3
```

Brute Force Solution
```
# Complete the minimumSwaps function below.
def minimumSwaps(arr):
    arr = [i-1 for i in arr] #shifting the index
    count = 0
    for i in range(len(arr)):
        ori, cur = i, arr[i]
        if ori != cur:
            count += 1
            k,j = i, arr.index(i)
            arr[k], arr[j] = arr[j], arr[k]
        
    return int(count)
 ```
 Hashmap
 ```
 # Complete the minimumSwaps function below.
def minimumSwaps(arr):
    swaps = 0
    tmp = {} 

    for i, val in enumerate(arr):
        tmp[val] = i #create a hashmap

    for i in range(len(arr)):
        # because they are consecutives, I can see if the number is where it belongs
        if arr[i] != i+1:
            swaps += 1
            t = arr[i]
            arr[i] = i+1
            arr[tmp[i+1]] = t

            # Switch also the tmp array, no need to change i+1 as it's already good now
            tmp[t] = tmp[i+1]

    return swaps
 ```
