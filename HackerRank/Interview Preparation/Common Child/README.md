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
    m = [[0]*(len(s2)+1) for _ in range(len(s1)+1)] # construct an (n+1)x(n+1) matrix
    
    for i,c in enumerate(s1,1): #enumerate, start =1
        for j,d in enumerate(s2,1):
            if c == d:
                m[i][j] = m[i-1][j-1]+1
            else:
                m[i][j] = max(m[i][j-1],m[i-1][j])
                   
    return m[-1][-1] #bottom right element in the matrix    
```
```
def commonChild(s1, s2):
  maxAt = {}

  for i1 in range(len(s1)):
    maxForI1 = 0
    for i2 in range(len(s2)):
      potentialSum = maxForI1 + 1

      # You might be tempted to use the max() function to simplify the next three lines,
      # but that makes the solution so much slower that several of the test cases fail.
      other = maxAt.get(i2, 0)
      if other > maxForI1:
        maxForI1 = other

      if s1[i1] == s2[i2]:
        maxAt[i2] = potentialSum

  return max(maxAt.values(), default=0)
```
