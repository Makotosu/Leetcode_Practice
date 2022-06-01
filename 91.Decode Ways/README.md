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
```
class Solution(object):
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        
        #dp[i] = dp[i+1] + dp[i+2]
        
        dp = {len(s):1}
        
        def dfs(i):
            if i in dp:
                return dp[i] 
            if s[i] == "0":
                return 0
            
            res = dfs(i+1)
            if (i+1 < len(s) and (s[i] =="1" or s[i] =="2" and s[i+1] in "0123456")):
                res += dfs(i+2)
            dp[i] = res
            return res
        
        return dfs(0)
```
```
class Solution(object):
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        
        #dp[i] = dp[i+1] + dp[i+2]
        
        dp = {len(s):1}
        for i in range(len(s) - 1, -1, -1):
            if s[i] == "0":
                dp[i] = 0
            else:
                dp[i] = dp[i+1]
            
            if (i+1 < len(s) and (s[i] =="1" or s[i] =="2" and s[i+1] in "0123456")):
                dp[i] += dp[i+2]
        return dp[0] 
```
