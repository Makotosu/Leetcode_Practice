It is New Year's Day and people are in line for the Wonderland rollercoaster ride. Each person wears a sticker indicating their initial position in the queue from 1 to n . Any person can bribe the person directly in front of them to swap positions, but they still wear their original sticker. One person can bribe at most two others.
Determine the minimum number of bribes that took place to get to a given queue order. Print the number of bribes, or, if anyone has bribed more than two people, print Too chaotic.
  
 ```
 Example
 Sample Input
STDIN       Function
-----       --------
2           t = 2
5           n = 5
2 1 5 3 4   q = [2, 1, 5, 3, 4]
5           n = 5
2 5 1 3 4   q = [2, 5, 1, 3, 4]

Sample Output
3
Too chaotic
```
```
def minimumBribes(q):
    # Write your code here
    bribe = 0
    q = [i-1 for i in q] #shift the index so that starts from o
    for i,o in enumerate(q):
        cur = i
        if (o-cur) >= 3:
            print("Too chaotic")
            return 

        for k in q[max(o-1,0):i]:
            if k >o:
                bribe += 1
    print(bribe)
```
