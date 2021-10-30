### Special String Again
A string is said to be a special string if either of two conditions is met:
All of the characters are the same, e.g. aaa.
All characters except the middle one are the same, e.g. aadaa.
A special substring is any substring of a string which meets one of those criteria. Given a string, determine how many special substrings can be formed from it.

```
Sample Input 0
5
asasd
Sample Output 0
7 
```

```
# Complete the substrCount function below.
def substrCount(n, s):
    result = 0
    i = 0
    
    #first case: consider same continuous substring
    while (i < n):
        char_count = 1
        while (i + 1 < n and s[i] == s[i+1]):
            i += 1
            char_count += 1
    
        result += int(char_count * (char_count + 1) / 2)
        i += 1
    
    #second case: consider substring with different middle
    for i in range(1, n):
        char_count = 1
        while (
            i + char_count < n and
            i - char_count >= 0 and
            s[i] != s[i-1] and
            s[i-char_count] == s[i+char_count] and
            s[i-1] == s[i-char_count]
        ):
            char_count += 1
    
        result += char_count - 1
    
    return result
```
