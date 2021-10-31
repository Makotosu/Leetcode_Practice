### Luck Balance

Lena is preparing for an important coding competition that is preceded by a number of sequential preliminary contests. Initially, her luck balance is 0. She believes in "saving luck", and wants to check her theory. Each contest is described by two integers, L[i] and T[i]:

```
Contest		L[i]	T[i]
1		5	1
2		1	1
3		4	0

STDIN       Function
-----       --------
6 3         n = 6, k = 3
5 1         contests = [[5, 1], [2, 1], [1, 1], [8, 1], [10, 0], [5, 0]]
2 1
1 1
8 1
10 0
5 0
Sample Output
29
```

```
def luckBalance(k, contests):
    # Write your code here
    res = 0
    L = []
    for (i,j) in contests:
        if j == 0:
            res += i
        else:
            L.append(i)
    
    L2 = sorted(L, reverse = True)
    for i in range(len(L2)):
        if i <= k-1:
            res += L2[i]
        else:
            res -= L2[i]
    return res
```
