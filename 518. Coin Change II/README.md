### 518. Coin Change II

https://leetcode.com/problems/coin-change-ii/description/

You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the number of combinations that make up that amount. If that amount of money cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer.

```
Example 1:

Input: amount = 5, coins = [1,2,5]
Output: 4
Explanation: there are four ways to make up the amount:
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1
```

```
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        dp = [[0]*(len(coins)+1) for i in range(amount + 1)]
        dp[0] = [1] *(len(coins)+1)

        for i in range(1, amount+1):
            for j in range(len(coins)-1, -1 , -1):
                dp[i][j] = dp[i][j+1]

                if i - coins[j] >= 0:
                    dp[i][j] += dp[i-coins[j]][j]

        return dp[-1][0]
        # Column: Amount 0, 1, 2, 3, 4, 5
        # Row: Coins: 1, 2, 5, 0
```



