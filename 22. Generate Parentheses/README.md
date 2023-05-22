### 22. Generate Parentheses

https://leetcode.com/problems/generate-parentheses/description/

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

Example 1:
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]

```
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n == 0:
            return []

        # Create a list to store the valid parentheses combinations  
        dp = [[] for i in range(n+1)]
        dp[0].append('')
        
        # We combine the valid parentheses combinations from dp[j] and dp[i-j-1] and add them to dp[i]
        for i in range(1, n+1):
            for j in range(i):
                for x in dp[j]:
                    for y in dp[i-j-1]:
                        dp[i].append('(' + x + ')' + y)
        return dp[n] 
```
