### Greedy Glorist

Greedy florist wants to sell flowers for more money, and created the following rules:
For a group of k customers to buy n flowers with associated cost [c[0], c[1], …c [n-1]]. First time buyer pay original price, second time buyer will have to pay twice the price, and third time buyer will have to pay third the price…
What’s the algorithm to calculate the minimum cost for the k poor customers?

```
Sample Input 0
3 3
2 5 6
Sample Output 0
13
```
```
def getMinimumCost(k, c):
    n = len(c)
    c.sort(reverse=True) # sort the price with decending order 
    cost = 0
    previous_purchase = 0
    for i in range(n):
        cost += (previous_purchase +1) * c[i]
        if (i+1)%k==0:
            previous_purchase += 1
    return cost
 ```
