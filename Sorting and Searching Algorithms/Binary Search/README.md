### Binary Search 

https://www.programiz.com/dsa/binary-search

```
# Iteration Method 

def BinarySearch(array, x):
  low, high = -1, len(array)

  while low+1 != high: 
    mid = (low + high) // 2

    if array[mid] == x:
      return mid

    elif array[mid] < x:
      low = mid

    else:
      high = mid

  return -1 
  # return low or high      
  
  
# Recursive Method 
def BinarySearch(array, x, low = -1, high = len(array)):

  if low + 1 != high: 
    mid = (low + high) // 2

    if array[mid] == x:
      return mid

    elif array[mid] < x:
      return BinarySearch(array, x, mid, high)

    else:
      return BinarySearch(array, x, low, mid)
      
  else: 
    return -1 

```

Time Complexity: O(log n) 
