# Day 13 - Python Programming

## Goal
Build core Python skills - the most important programming language across this entire roadmap, used in automation, security scripting, AI/LLM work, and more.

---

## 1. Syntax & Data Types

```python
# Variables and basic types
name = "Tharsan"          # str
age = 21                    # int
height = 5.9                 # float
is_student = True             # bool

# Collections
my_list = [1, 2, 3]              # list - ordered, mutable
my_tuple = (1, 2, 3)               # tuple - ordered, immutable
my_dict = {"key": "value"}           # dict - key-value pairs
my_set = {1, 2, 3}                    # set - unordered, unique values
```

## 2. Control Flow & Functions

```python
# Conditionals
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teen")
else:
    print("Child")

# Loops
for item in my_list:
    print(item)

i = 0
while i < 5:
    print(i)
    i += 1

# Functions
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Tharsan"))
print(greet("Tharsan", "Hi"))
```

## 3. OOP Concepts

```python
class Device:
    def __init__(self, name, ip):
        self.name = name
        self.ip = ip

    def display_info(self):
        return f"{self.name} - {self.ip}"

class Router(Device):           # inheritance
    def __init__(self, name, ip, ports):
        super().__init__(name, ip)
        self.ports = ports

r = Router("CoreRouter", "192.168.1.1", 24)
print(r.display_info())
```

Core OOP concepts: Class, Object, Inheritance, Encapsulation, Polymorphism.

## 4. File Handling

```python
# Writing
with open("notes.txt", "w") as f:
    f.write("Day 13 - Python\n")

# Reading
with open("notes.txt", "r") as f:
    content = f.read()
    print(content)

# Appending
with open("notes.txt", "a") as f:
    f.write("Added more content\n")
```

`with` automatically closes the file, even if an error occurs - the standard practice over manual `open()`/`close()`.

## 5. Modules & Libraries

```python
import os
import sys
import json
import requests        # third-party, install via pip

print(os.getcwd())
data = json.loads('{"key": "value"}')
```

## 6. Security Scripting (Automation, Parsing)

```python
import re

log_line = "2026-06-21 10:23:45 FAILED login from 192.168.1.50"
match = re.search(r'\d+\.\d+\.\d+\.\d+', log_line)
if match:
    print("IP found:", match.group())

# Simple log parser counting failed logins
def count_failed_logins(filepath):
    count = 0
    with open(filepath) as f:
        for line in f:
            if "FAILED" in line:
                count += 1
    return count
```

---

## Interview Questions

**Q1. Difference between a list and a tuple?**
A list is mutable (can be changed after creation); a tuple is immutable (cannot be changed).

**Q2. What does `with open(...)` do that plain `open()` doesn't?**
It automatically closes the file when the block ends, even if an exception occurs, preventing resource leaks.

**Q3. What is inheritance in OOP?**
A mechanism where a class (child) derives properties and methods from another class (parent), enabling code reuse.

**Q4. Why is Python commonly used in security scripting?**
Its simple syntax, extensive libraries (requests, re, os), and strong support for automation and parsing make it efficient for writing tools quickly.

## Key Takeaways
- Learned Python syntax, data types, and collections
- Learned control flow and function definition
- Learned core OOP concepts with a practical example
- Learned file handling using `with`
- Learned module imports and a basic security scripting example (log parsing with regex)
