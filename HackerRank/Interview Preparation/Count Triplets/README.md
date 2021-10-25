### Count Triplets
You are given an array and you need to find number of tripets of indices (i,j,k)  such that the elements at those indices are in geometric progression for a given common ratio r and i <j <k .

```
Sample Input 0
4 2
1 2 2 4
Sample Output 0
2
```

```
from collections import Counter
# Complete the countTriplets function below.
def countTriplets(arr, r):
    newarr = [int(math.log(i,r)) for i in arr] #take log first
    dict = Counter(newarr)
    count = 0
    for i in range(max(newarr) - 1):
        count += dict[i] * dict[i+1] * dict[i+2]
    return count  
```
```
from collections import Counter
# Complete the countTriplets function below.
def countTriplets(arr, r):
    a = Counter(arr)
    b = Counter()
    s = 0
    for i in arr:
        j = i//r
        k = i*r
        a[i]-=1
        if b[j] and a[k] and i%r == 0:
            s+=b[j]*a[k]
        b[i]+=1
    return s    
 ```
