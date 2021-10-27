### Merge Sort: Counting Inversions

Brute Force
```
def getInvCount(arr, n):

	inv_count = 0
	for i in range(n):
		for j in range(i + 1, n):
			if (arr[i] > arr[j]):
				inv_count += 1

	return inv_count
```

Merge Sort
```
def sort_pair(arr0, arr1):
    if len(arr0) > len(arr1):
        return arr1, arr0
    else:
        return arr0, arr1
    
def merge(arr0, arr1):
    inversions = 0
    result = []
    while len(arr0) > 0 and len(arr1) > 0:
        if arr0[0] <= arr1[0]:
            result.append(arr0.pop(0))
        else:
            # count the inversion right here: add the length of left array
            inversions += len(arr0)
            result.append(arr1.pop(0))
            
    if len(arr0) == 0:
        result += arr1
    elif len(arr1) == 0:
        result += arr0
        
    return result, inversions

def sort(arr):
    length = len(arr)
    mid = length//2
    if length >= 2:
        sorted_0, counts_0 = sort(arr[:mid])
        sorted_1, counts_1 = sort(arr[mid:])
        result, counts = merge(sorted_0, sorted_1)
        return result, counts + counts_0 + counts_1
    else:
        return arr, 0

def count_inversions(a):
    final_array, inversions = sort(a)
    # print(final_array)
    return inversions
      

t = int(input().strip())
for a0 in range(t):
    n = int(input().strip())
    arr = list(map(int, input().strip().split(' ')))
    print(count_inversions(arr))
```
