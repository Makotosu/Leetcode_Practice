### Repeated String
There is a string s , of lowercase English letters that is repeated infinitely many times. Given an integer n, find and print the number of letter a's in the first  letters of the infinite string.

```
Sample Input 
aba
10
Sample Output 
7
```
```
def repeatedString(s, n):
    # Write your code here
    l = len(s)
    per = s.count('a')
    count = int((n/l)) * per
    remain = n % l
    for i in range(remain):
        if s[i] == 'a':
            count += 1
    return count 
```
