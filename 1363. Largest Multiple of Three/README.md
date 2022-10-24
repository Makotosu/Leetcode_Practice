### 1363. Largest Multiple of Three

https://leetcode.com/problems/largest-multiple-of-three/

Given an array of digits digits, return the largest multiple of three that can be formed by concatenating some of the given digits in any order. If there is no answer return an empty string.

Since the answer may not fit in an integer data type, return the answer as a string. Note that the returning answer must not contain unnecessary leading zeros.

···
Example 1:

Input: digits = [8,1,9]
Output: "981"
···

···
class Solution:
    def largestMultipleOfThree(self, digits: List[int]) -> str:
        s = sum(digits)
        d = {x:[] for x in range(0, 3)}
        
        for x in digits:
            d[x % 3].append(x)
            
        if s%3 == 0:
            d1 = sorted(digits)[::-1]
            output = ''.join(str(x) for x in d1)
            return str(int(output))
        else:
            m = s %3
            if d[m] != []:
                digits.remove(min(d[m]))
                digits = sorted(digits)[::-1]
                output = ''.join(str(x) for x in digits)
                return output if output == '' else str(int(output))
                              
            elif d[m] == [] and len(d[3-m]) >= 2:
                digits.remove(min(d[3-m]))
                d[3-m].remove(min(d[3-m]))
                digits.remove(min(d[3-m]))
                digits = sorted(digits)[::-1]
                output = ''.join(str(x) for x in digits)
                return output if output == '' else str(int(output))
            else:
                return ''
···                                              
