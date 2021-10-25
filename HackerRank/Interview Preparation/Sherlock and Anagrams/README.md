### Sherlock and Anagrams

Two strings are anagrams of each other if the letters of one string can be rearranged to form the other string. Given a string, find the number of pairs of substrings of the string that are anagrams of each other.
```
Sample Input 0
2
abba
abcd
Sample Output 0
4
0
```
```
from collections import Counter

def sherlockAndAnagrams(s):
    count = Counter(("".join(sorted(s[j:j+i])) for i in range(1,len(s)) for j in range(0,len(s)-i+1) ))
    return sum(sum(range(i)) for i in count.values())
```
