### Array Manipulation
Starting with a 1-indexed array of zeros and a list of operations, for each operation add a value to each the array element between two given indices, inclusive. Once all operations have been performed, return the maximum value in the array.

```
Sample Input
5 3
1 2 100
2 5 100
3 4 100
Sample Output
200
```
Brute Force Solution
```
def arrayManipulation(n, queries):
    arr = [0]*n
    for i in queries:
        for j in range(i[0], i[1] + 1):
            arr[j - 1] += i[-1]
    return max(arr)
```

```
def arrayManipulation(n, queries):
    arr = [0]*n
    for i in queries:
        arr[i[0] - 1] += i[2]
        if i[1] != len(arr):
            arr[i[1]] -= i[2]
    maxval = 0
    itt = 0

    for q in arr:
        itt += q
        if itt > maxval:
            maxval = itt
    return maxval
```
