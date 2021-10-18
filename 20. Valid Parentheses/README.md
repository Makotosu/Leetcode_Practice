### 20. Valid Parentheses

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

```
Example
Input: s = "()"
Output: true

Input: s = "([)]"
Output: false
```

    def isValid(self, s: str) -> bool:
        while len(s) > 0:
            l = len(s)
            s = s.replace('()','').replace('{}','').replace('[]','')
            if l == len(s): 
                return False
        return True
        
 ```
    def isValid(self, s: str) -> bool:
        stack = []
        closeToOpen = {")":"(", "]":"[", "}":"{"}
        
        for c in s:
            if c in closeToOpen:
                if stack and stack[-1] == closeToOpen[c]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(c)
                
        return True if not stack else False
