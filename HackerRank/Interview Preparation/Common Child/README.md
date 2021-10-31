### Common Child

A string is said to be a child of a another string if it can be formed by deleting 0 or more characters from the other string. Letters cannot be rearranged. Given two strings of equal length, what's the longest string that can be constructed such that it is a child of both?

```
Sample Input
HARRY
SALLY
Sample Output
 2
```
```
def commonChild(s1, s2):
    # Write your code here
    c1 = Counter(s1)
    c2 = Counter(s2)
    c3 = c1 - (c1 - c2) # common term
    l = list(c3.keys()) # element in l is ordered as in string s1
    result = 0
    
    for i in range(1, len(l)):
        if s2.index(l[i-1]) <= s2.index(l[i]):
            result += 1
    return result
```
Model Solution
```
def commonChild(s1, s2):
    m = [[0]*(len(s2)+1) for _ in range(len(s1)+1)]
    for i,c in enumerate(s1,1):
        for j,d in enumerate(s2,1):
            if c == d:
                m[i][j] = m[i-1][j-1]+1
            else:
                m[i][j] = max(m[i][j-1],m[i-1][j])
                   
    return m[-1][-1]
```

