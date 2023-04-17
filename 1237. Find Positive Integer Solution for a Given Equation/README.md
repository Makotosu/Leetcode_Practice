### 1237. Find Positive Integer Solution for a Given Equation

https://leetcode.com/problems/find-positive-integer-solution-for-a-given-equation/description/

Given a callable function f(x, y) with a hidden formula and a value z, reverse engineer the formula and return all positive integer pairs x and y where f(x,y) == z. You may return the pairs in any order.

While the exact formula is hidden, the function is monotonically increasing, i.e.:

f(x, y) < f(x + 1, y)
f(x, y) < f(x, y + 1)
The function interface is defined like this:

interface CustomFunction {
public:
  // Returns some positive integer f(x, y) for two positive integers x and y based on a formula.
  int f(int x, int y);
};



```
"""
   This is the custom function interface.
   You should not implement it, or speculate about its implementation
   class CustomFunction:
       # Returns f(x, y) for any given positive integers x and y.
       # Note that f(x, y) is increasing with respect to both x and y.
       # i.e. f(x, y) < f(x + 1, y), f(x, y) < f(x, y + 1)
       def f(self, x, y):
  
"""
class Solution:
    def findSolution(self, customfunction: 'CustomFunction', z: int) -> List[List[int]]:

        output = [] 

        x_init, x_large = 1, z+1

        for x in range(x_init, x_large):  #fix x 
            y_low, y_high = 0, z+1

            while y_low +1 < y_high: 
                y_mid = (y_low + y_high) // 2

                if customfunction.f(x, y_mid) == z:
                    output.append([x, y_mid])
                    break 
                elif customfunction.f(x, y_mid) < z:
                    y_low = y_mid

                else:
                    y_high = y_mid

        return output 
```
