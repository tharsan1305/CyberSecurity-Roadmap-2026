# Day 14 - Lab: DSA Practice

## Objective
Implement and test core data structures and algorithms in Python.

## Task 1: Implement a Stack-Based Bracket Checker
A classic stack use case - checking if brackets in a string are balanced:
```python
def is_balanced(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in '([{':
            stack.append(char)
        elif char in ')]}':
            if not stack or stack.pop() != pairs[char]:
                return False
    return len(stack) == 0

print(is_balanced("({[]})"))   # True
print(is_balanced("({[}])"))    # False
```

## Task 2: Implement and Test Binary Search
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

sorted_list = [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
print(binary_search(sorted_list, 23))   # should return index 5
print(binary_search(sorted_list, 100))   # should return -1
```

## Task 3: Build and Traverse a Simple Graph
```python
graph = {
    "Workstation": ["Switch"],
    "Switch": ["Router"],
    "Router": ["Firewall"],
    "Firewall": ["Internet"],
    "Internet": []
}

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

print(bfs(graph, "Workstation"))
```

## Task 4: Compare Sorting Performance
```python
import time
import random

data = [random.randint(1, 10000) for _ in range(2000)]

def bubble_sort(arr):
    arr = arr.copy()
    n = len(arr)
    for i in range(n):
        for j in range(n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr

start = time.time()
bubble_sort(data)
print(f"Bubble sort time: {time.time() - start:.4f}s")

start = time.time()
sorted(data)   # Python's built-in Timsort, O(n log n)
print(f"Built-in sort time: {time.time() - start:.4f}s")
```

## Results
| Item | Value |
|---|---|
| Bracket checker works (Y/N) | |
| Binary search results correct (Y/N) | |
| BFS traversal order | |
| Bubble sort time | |
| Built-in sort time | |

## Screenshots
```
![Bracket Checker](Screenshots/bracket-checker.png)
![Sort Performance](Screenshots/sort-performance.png)
```

## Lab Summary
Note the actual time difference between bubble sort and built-in sort on 2000 items - this makes Big O concrete rather than abstract.
