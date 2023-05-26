### Depth First Search (DFS)

https://www.programiz.com/dsa/graph-dfs 

```
# DFS algorithm in Python


# DFS algorithm
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)

    print(start)

    for next in graph[start] - visited:
        dfs(graph, next, visited)
    return visited


graph = {'0': set(['1', '2']),
         '1': set(['0', '3', '4']),
         '2': set(['0']),
         '3': set(['1']),
         '4': set(['2', '3'])}

dfs(graph, '0')
```

dfs algorithm traversal of a tree using recursion 

https://www.geeksforgeeks.org/dfs-traversal-of-a-tree-using-recursion/
```
e.g. 
1
2, 3
4 5,

Therefore, the Depth First Traversals of this Tree will be:

Inorder: 4 2 5 1 3
Preorder: 1 2 4 5 3
Postorder: 4 5 2 3 1
```

```
# Inorder Traversal 
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key
 
 def printInorder(node):
    if node:
        printInorder(node.left)
        print(node.val)
        printInorder(node.right)     
```        


```
# Preorder Traversal 
def printPreorder(node):
    if node:
        print(node.val)
        printPreorder(node.left)
        printPreorder(node.right)
```

```
# Postorder Traversal 
def printPostorder(node):
    if node:
        printPostorder(node.left)
        printPostorder(node.right)
        print(node.val)
```
