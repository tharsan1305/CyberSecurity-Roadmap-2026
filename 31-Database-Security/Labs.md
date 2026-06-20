# Day 31 - Lab: Database Security

## Objective
Practice identifying and preventing SQL Injection, and configuring secure database access.

## Task 1: Demonstrate SQL Injection (Safe, Local Lab Only)
Create a small Python script with an intentionally vulnerable query:
```python
import sqlite3

conn = sqlite3.connect(":memory:")
cur = conn.cursor()
cur.execute("CREATE TABLE users (username TEXT, password TEXT)")
cur.execute("INSERT INTO users VALUES ('admin', 'secret123')")

# VULNERABLE - string concatenation
user_input = "' OR '1'='1"
query = f"SELECT * FROM users WHERE username = '{user_input}'"
print("Query:", query)
result = cur.execute(query).fetchall()
print("Result:", result)
```
Observe: the injection returns the admin row despite no valid username being provided.

## Task 2: Fix It with Parameterized Queries
```python
safe_input = "' OR '1'='1"
cur.execute("SELECT * FROM users WHERE username = ?", (safe_input,))
print("Safe Result:", cur.fetchall())
```
Observe: this time, the malicious input is treated as a literal string and returns no results.

## Task 3: Configure SSL-Required Database User (MySQL)
```sql
CREATE USER 'secure_user'@'%' IDENTIFIED BY 'StrongPass123' REQUIRE SSL;
GRANT SELECT ON library.* TO 'secure_user'@'%';
```
Attempt to connect without SSL and observe the connection being rejected (if SSL is properly enforced on the server).

## Task 4: Review Database Logs
Enable general query logging (MySQL) or check PostgreSQL logs, and identify your own test queries from Task 1-3 in the log output.

## Results
| Item | Value |
|---|---|
| SQLi reproduced successfully (Y/N) | |
| Parameterized query blocked injection (Y/N) | |
| SSL-required user created (Y/N) | |
| Queries visible in logs (Y/N) | |

## Screenshots
```
![SQLi Demonstration](Screenshots/sqli-demo.png)
![Parameterized Fix](Screenshots/parameterized-fix.png)
![Query Logs](Screenshots/query-logs.png)
```

## Lab Summary
Write 2-3 lines on how it felt to see the injection actually work, and why parameterized queries are considered the primary defense rather than just input filtering.
