14. Longest Common Prefix

https://leetcode.com/problems/longest-common-prefix/description/?envType=study-plan&id=level-2

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

 
```
Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
```

```
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        res = ''

        for i in zip(*strs):
            if len(set(i)) == 1:
                res += i[0] 
            else:
                break 

        return res 
```          
