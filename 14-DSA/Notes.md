# Day 14 - Data Structures & Algorithms (DSA)

## Goal
Build foundational DSA knowledge - important for technical interviews and for writing efficient security/automation tooling.

---

## 1. Arrays, Strings, Linked Lists

**Array**: fixed-size, ordered collection, O(1) access by index.
```python
arr = [10, 20, 30, 40]
print(arr[2])    # O(1) access
```

**String**: sequence of characters, often treated as an array of characters for algorithm purposes.

**Linked List**: a sequence of nodes, each pointing to the next - O(1) insertion at head, but O(n) access by index (no direct indexing).
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_head(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
```

## 2. Stacks & Queues

**Stack**: Last-In-First-Out (LIFO).
```python
stack = []
stack.append(1)    # push
stack.append(2)
stack.pop()          # pop -> returns 2
```

**Queue**: First-In-First-Out (FIFO).
```python
from collections import deque
queue = deque()
queue.append(1)        # enqueue
queue.append(2)
queue.popleft()          # dequeue -> returns 1
```

Real-world relevance: stacks are used in undo functionality and function call tracking; queues are used in task scheduling and breadth-first traversal.

## 3. Trees & Graphs

**Tree**: hierarchical structure with a root node and child nodes, no cycles. Binary Tree: each node has at most 2 children.

**Graph**: nodes (vertices) connected by edges, can have cycles. Used to model networks, dependencies, relationships - directly relevant to Active Directory attack paths (BloodHound visualizes AD as a graph) and network topology.

```python
graph = {
    "A": ["B", "C"],
    "B": ["D"],
    "C": ["D"],
    "D": []
}

# Simple BFS traversal
from collections import deque
def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    order = []
    while queue:
        node = queue.popleft()
        order.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return order

print(bfs(graph, "A"))
```

## 4. Sorting & Searching Algorithms

**Bubble Sort** (simple, O(n²)):
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

**Binary Search** (requires sorted data, O(log n)):
```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

## 5. Time/Space Complexity (Big O)

Common complexities, fastest to slowest:
```
O(1)        constant - array index access
O(log n)    logarithmic - binary search
O(n)         linear - single loop through data
O(n log n)    linearithmic - efficient sorting (merge sort, quicksort average case)
O(n²)          quadratic - nested loops (bubble sort)
O(2^n)           exponential - brute force recursive problems
```

---

## Interview Questions

**Q1. Difference between a Stack and a Queue?**
Stack is LIFO (Last-In-First-Out); Queue is FIFO (First-In-First-Out).

**Q2. What is the time complexity of Binary Search, and what's required to use it?**
O(log n), and the data must be sorted beforehand.

**Q3. Why are graphs relevant to cybersecurity?**
They model relationships and paths - e.g., Active Directory attack path analysis (BloodHound) represents users, groups, and permissions as a graph to find privilege escalation paths.

**Q4. What's the time complexity of Bubble Sort, and why is it inefficient for large datasets?**
O(n²) - it has nested loops comparing every pair, making it slow for large inputs compared to O(n log n) algorithms.

## Key Takeaways
- Learned arrays, strings, and linked lists with implementation examples
- Learned stacks (LIFO) and queues (FIFO) with practical use cases
- Learned trees and graphs, including their cybersecurity relevance (AD attack paths)
- Learned bubble sort and binary search algorithms
- Learned Big O notation for evaluating algorithm efficiency
