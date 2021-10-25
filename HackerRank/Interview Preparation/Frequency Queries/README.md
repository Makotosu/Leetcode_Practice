### Frequency Queries
You are given a queries. Each query is of the form two integers described below: 
### (1,x) : Insert x in your data structure. 
### (2,y) : Delete one occurence of y from your data structure, if present. 
### (3,z)  : Check if any integer is present whose frequency is exactly z. If yes, print 1 else 0.
### The queries are given in the form of a 2-D array queries of size q where queries[i][0] contains the operation, and queries[i][1] contains the data element.

```
Sample Input 0
8
1 5
1 6
3 2
1 10
1 10
1 6
2 5
3 2
Sample Output 0
0
1
```

```
from collections import Counter

def freqQuery(queries):
    c = Counter()
    d = Counter()
    for x,y in queries:
        v = c[y]
        if x==1:
            d[v] = max(d[v]-1,0)
            d[v+1] += 1
            c[y] = v+1
        elif x==3:
            yield 1 if d[y] else 0
        elif v:
            d[v] = max(d[v]-1,0)
            d[v-1] += 1
            c[y] = v-1
 ```
 
