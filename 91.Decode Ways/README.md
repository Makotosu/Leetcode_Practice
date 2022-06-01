### Python 
 
https://leetcode.com/problems/decode-ways/

A message containing letters from A-Z can be encoded into numbers using the following mapping:

'A' -> "1"

'B' -> "2"

...

'Z' -> "26"

```
Example 1:

Input: s = "12"
Output: 2
Explanation: "12" could be decoded as "AB" (1 2) or "L" (12).
```

Almost correct:
```
class Solution(object):
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        n = len(s) 
        s_list = [int(s[i]) for i in range(n)]

        null = []
        for i in range(n):
            if s_list[i] == 0:
                null.append(i) #create a list storing the index of 0 in s 
        
        output = [0] *n
        output[0] = 1
            
        for i in range(1, n):
            if i not in null and i+1 not in null:
                if 10*s_list[i-1] + s_list[i] <= 26:
                    output[i] = output[i-1] + 1
                else:
                    output[i] = output[i-1]
                    
            elif i not in null and i+1 in null:
                output[i] = output[i-1] 
            else:
                output[i] = 0
                
        res = 1
        if null == []:
            res = output[-1]
        elif null[0] == 0:
            res = 0
        else:
            for i in null:
                res *= output[i-1]
            if output[-1] == 0:
                res = res
            else:
                res *= output[-1]
            
        return res
```
