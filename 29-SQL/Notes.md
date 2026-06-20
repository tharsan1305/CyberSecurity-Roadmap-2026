# Day 29 - SQL

## Goal
Build practical SQL skills - essential not just for database work, but for log analysis, SIEM querying, and understanding SQL injection (OWASP Top 10) later in the roadmap.

---

## 1. DDL (Data Definition Language)
Commands that define/modify database structure.

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(100),
    Salary DECIMAL(10,2)
);

ALTER TABLE Employees ADD Department VARCHAR(50);

DROP TABLE Employees;
```

## 2. DML (Data Manipulation Language)
Commands that manipulate data within tables.

```sql
INSERT INTO Employees (EmpID, Name, Salary) VALUES (1, 'Tharsan', 50000);

UPDATE Employees SET Salary = 55000 WHERE EmpID = 1;

DELETE FROM Employees WHERE EmpID = 1;
```

## 3. DQL (Data Query Language) - SELECT, JOINS, Subqueries

### Basic SELECT
```sql
SELECT Name, Salary FROM Employees;
SELECT * FROM Employees WHERE Salary > 50000;
SELECT * FROM Employees ORDER BY Salary DESC;
```

### JOINS
```sql
-- INNER JOIN: only matching rows in both tables
SELECT Employees.Name, Departments.DeptName
FROM Employees
INNER JOIN Departments ON Employees.DeptID = Departments.DeptID;

-- LEFT JOIN: all rows from left table, matched where possible
SELECT Employees.Name, Departments.DeptName
FROM Employees
LEFT JOIN Departments ON Employees.DeptID = Departments.DeptID;
```

### Subqueries
```sql
SELECT Name FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```

## 4. Aggregate Functions & Grouping

```sql
SELECT COUNT(*) FROM Employees;
SELECT AVG(Salary) FROM Employees;
SELECT MAX(Salary), MIN(Salary) FROM Employees;
SELECT SUM(Salary) FROM Employees;

SELECT Department, AVG(Salary)
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 50000;
```

Note: `WHERE` filters rows before grouping; `HAVING` filters groups after aggregation - a common interview distinction.

---

## Interview Questions

**Q1. Difference between WHERE and HAVING?**
WHERE filters individual rows before grouping; HAVING filters groups after aggregation (e.g., after GROUP BY).

**Q2. Difference between INNER JOIN and LEFT JOIN?**
INNER JOIN returns only matching rows from both tables; LEFT JOIN returns all rows from the left table plus matched rows from the right (NULL where no match).

**Q3. What's the difference between DELETE and DROP?**
DELETE removes rows from a table (data only, structure remains); DROP removes the entire table structure along with its data.

**Q4. What is a subquery?**
A query nested inside another query, often used to filter results based on a calculated value (e.g., comparing against an average).

## Key Takeaways
- Learned DDL (CREATE, ALTER, DROP) for structure changes
- Learned DML (INSERT, UPDATE, DELETE) for data manipulation
- Learned DQL: SELECT, JOINS (INNER/LEFT), subqueries
- Learned aggregate functions and GROUP BY/HAVING usage
