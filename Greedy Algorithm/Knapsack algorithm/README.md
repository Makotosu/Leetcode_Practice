### Knapsack Algorithm 

https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/

```
0/1 knapsack 

The maximum value obtained from ‘N’ items is the max of the following two values. 

Maximum value obtained by N-1 items and W weight (excluding nth item)
Value of nth item plus maximum value obtained by N-1 items and (W – weight of the Nth item) [including Nth item].
If the weight of the ‘Nth‘ item is greater than ‘W’, then the Nth item cannot be included and Case 1 is the only possibility.

f(i, j): maximum utility when you have j capacity and have already bought i items. 

Then f(i, j) = max{f(i-1, j), f(i-1, j-w(i)) + v(i)}
```
```
# A naive recursive implementation
# of 0-1 Knapsack Problem

# Returns the maximum value that
# can be put in a knapsack of
# capacity W


def knapSack(W, wt, val, n):

	# Base Case
	if n == 0 or W == 0:
		return 0

	# If weight of the nth item is
	# more than Knapsack of capacity W,
	# then this item cannot be included
	# in the optimal solution
	if (wt[n-1] > W):
		return knapSack(W, wt, val, n-1)

	# return the maximum of two cases:
	# (1) nth item included
	# (2) not included
	else:
		return max(val[n-1] + knapSack(W-wt[n-1], wt, val, n-1),
				knapSack(W, wt, val, n-1))

# end of function knapSack
# Time Complexity: O(2^N)


# Driver Code
if __name__ == '__main__':
	profit = [60, 100, 120]
	weight = [10, 20, 30]
	W = 50
	n = len(profit)
	print knapSack(W, weight, profit, n)
```

```
# A Dynamic Programming based Python
# Program for 0-1 Knapsack problem
# Returns the maximum value that can
# be put in a knapsack of capacity W


def knapSack(W, wt, val, n):
	K = [[0 for x in range(W + 1)] for x in range(n + 1)]

	# Build table K[][] in bottom up manner
	for i in range(n + 1):
		for j in range(W + 1):
			if i == 0 or j == 0:
				K[i][j] = 0
			elif wt[i-1] <= w:
				K[i][j] = max(val[i-1]+ K[i-1][w-wt[i-1]],K[i-1][j])
			else:
				K[i][j] = K[i-1][j]

	return K[n][W]
# Time Complexity: O(N*W)

# Driver code
if __name__ == '__main__':
	profit = [60, 100, 120]
	weight = [10, 20, 30]
	W = 50
	n = len(profit)
	print(knapSack(W, weight, profit, n))

```
