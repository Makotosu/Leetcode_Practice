### Fraudulent Activity Notifications

HackerLand National Bank has a simple policy for warning clients about possible fraudulent account activity. If the amount spent by a client on a particular day is greater than or equal to  the client's median spending for a trailing number of days, they send the client a notification about potential fraud. The bank doesn't send the client any notifications until they have at least that trailing number of prior days' transaction data.
```
Sample Input 0
STDIN               Function
-----               --------
9 5                 expenditure[] size n =9, d = 5
2 3 4 2 3 6 8 4 5   expenditure = [2, 3, 4, 2, 3, 6, 8, 4, 5]

Sample Output 0
2
```

```
def findMedian(counter, d):
    count = 0
    median = 0

    if d%2 != 0:
        for i in range(len(counter)):
            count += counter[i]

            if count > d//2:
                median = i
                break
            
    else:
        first = 0
        second = 0

        for i, _ in enumerate(counter):
            count += counter[i]
            
            if first == 0 and count >= d//2:
                first = i
                
            if second == 0 and count >= d//2 + 1:
                second = i
                break
            
        median = (first+second) / 2
        
    return median


def activityNotifications(expenditure, d):
    count = 0
    counter = [0]*201
    
    for exp in range(d):
        counter[expenditure[exp]] += 1

    for i in range(d, len(expenditure)):
        new = expenditure[i]
        old = expenditure[i-d]
        median = findMedian(counter, d)
        
        if new >= 2*median:
            count += 1
            
        counter[old] -= 1
        counter[new] += 1
        
    return count
```
