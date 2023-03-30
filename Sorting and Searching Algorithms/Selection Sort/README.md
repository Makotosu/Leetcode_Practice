### Selection Sort 

https://www.programiz.com/dsa/selection-sort

 Selects the smallest element from an unsorted list in each iteration 
 and places that element at the beginning of the unsorted list.
 
 ```
 def selectionSort(array):
    size = len(array)
   
    for step in range(size):
        min_idx = step

        for i in range(step + 1, size):
         
            # to sort in descending order, change > to < in this line
            # select the minimum element in each loop
            if array[i] < array[min_idx]:
                min_idx = i
         
        # put min at the correct position
        (array[step], array[min_idx]) = (array[min_idx], array[step])
```

Time Complexity: O(n^2)

Space Complexity: O(1)
