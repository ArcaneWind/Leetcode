# Basic Knowledge

## 1.Data storage methods

### 1.1 Array

* Continuous data storage
* Can be quickly searched by index
* More storage-efficient compared to linked lists
* Array resizing requires allocating new space and then copying the data, with a time complexity of O(n)
* Insertion and deletion require moving all subsequent data, with a time complexity of O(n)

### 1.2 Linked List

* The time complexity of inserting or deleting an element is O(1)
* Cannot be randomly accessed
* Each element must store pointers to the positions of the previous and next elements, consuming relatively more storage space

## 2.Classic traversal methods of data structures

### 2.1 Array

```python
def traverse(arr: List[int]):
    for i in range(len(arr)):
        # Iterative access arr[i]
```

### 2.2 Linked List

```python
# Singly linked list node
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None

def traverse(head: ListNode) -> None:
    p = head
    while p is not None:
        # Iterative access p.val
        p = p.next

def traverse(head: ListNode) -> None:
    # Recursive access head.val
    traverse(head.next)
```

### 2.3 Binary tree

```python
# Binary tree node
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
        
def traverse(root: TreeNode):
    # Pre-order position
    traverse(root.left)
    # In-order position
    traverse(root.right)
    # Post-order position
```

### 2.4 N-array tree

```python
# N-array tree node
class TreeNode:
    val: int
    children: List[TreeNode]

def traverse(root: TreeNode) -> None:
    for child in root.children:
        traverse(child)
```

### 2.5 DFS

``` python
class Graph:
    def __init__(self):
        self.nodes = {}  # key: node label, value: list of neighbors

    def add_edge(self, u, v):
        if u in self.nodes:
            self.nodes[u].append(v)
        else:
            self.nodes[u] = [v]
        # If it is an undirected graph,also need to add the edge from v to u
        # If the graph is directed, then the following line is not needed
        # self.nodes[v].append(u)

def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start) 
    for next in graph.nodes.get(start, []):
        if next not in visited:
            dfs(graph, next, visited)
```

### 2.6 BFS

``` py
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    
    while queue:
        vertex = queue.popleft()
        if vertex not in visited:
            print(vertex)
            visited.add(vertex)
            queue.extend(set(graph.nodes.get(vertex, [])) - visited)

```

