### Max Min

You will be given a list of integers, arr, and a single integer k. You must create an array of length k from elements of arr such that its unfairness is minimized. Call that array arr'. Unfairness of an array is calculated as
max(arr') - min(arr')

```
Sample Input 0
7
3
10
100
300
200
1000
20
30
Sample Output 0
20
```
```
def maxMin(k, arr):
    # Write your code here
    if k == 0:
        out = 0 
    else:
        ar = sorted(arr)
        dif = [ar[i+1] - ar[i] for i in range(len(ar)-1)]
        s = []
        for i in range(len(dif)-k+2):
            s.append(sum(dif[i:i+k-1]))
        out = min(s)
      
    return out
```
