### 22. Generate Parentheses

https://leetcode.com/problems/generate-parentheses/description/

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

```
Example 1:
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

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
        # Time complexity of this solution is O(n^2 * 2^n)
```

```
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
    
        def backtrack(left_count, right_count, current_str, result):
        # Base case: all parentheses used
            if left_count == 0 and right_count == 0:
                result.append(current_str)
                return

            # If there are remaining left parentheses, add one and recurse
            if left_count > 0:
                backtrack(left_count - 1, right_count, current_str + '(', result)

            # If there are more left parentheses than right parentheses, add a right parenthesis and recurse
            if left_count < right_count:
                backtrack(left_count, right_count - 1, current_str + ')', result)
                
        result = []
        backtrack(n, n, '', result)
        return result
```        
    

        
