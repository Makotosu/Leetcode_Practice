### 121. Best Time to Buy and Sell Stock
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

```
Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```
Brute Force
```
def maxProfit(self, prices: List[int]) -> int:
        res = 0
        
        for l in range(len(prices)):
            for r in range(l+1, len(prices)):
                profit = prices[r] - prices[l]
                res = max(res,profit)
        
        return res
 ```
Two Pointer
```
    def maxProfit(self, prices: List[int]) -> int:
        res = 0
        l, r = 0,1
        
        while r < len(prices):
            if prices[l] < prices[r]:
                profit = prices[r] - prices[l]
                res = max(res, profit)
            else:
                l = r
            r +=1
        
        return res
    ```
