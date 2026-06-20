# Day 29 - Lab: SQL Practice

## Objective
Practice DDL, DML, DQL, JOINs, and aggregate functions using a hands-on database.

## Setup
Using MySQL/PostgreSQL from Day 28, or a free online SQL sandbox (e.g., sqliteonline.com, DB Fiddle) if no local install.

## Task 1: Create Tables (DDL)
```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(100)
);

CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(100),
    Salary DECIMAL(10,2),
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
);
```

## Task 2: Insert Sample Data (DML)
```sql
INSERT INTO Departments VALUES (1, 'Engineering'), (2, 'Sales');
INSERT INTO Employees VALUES 
(1, 'Tharsan', 55000, 1),
(2, 'Kumar', 48000, 2),
(3, 'Priya', 62000, 1);
```

## Task 3: Query Practice (DQL)
```sql
-- All employees earning above average
SELECT Name, Salary FROM Employees WHERE Salary > (SELECT AVG(Salary) FROM Employees);

-- Join with department names
SELECT Employees.Name, Departments.DeptName
FROM Employees JOIN Departments ON Employees.DeptID = Departments.DeptID;

-- Average salary per department
SELECT DeptName, AVG(Salary) AS AvgSalary
FROM Employees JOIN Departments ON Employees.DeptID = Departments.DeptID
GROUP BY DeptName;
```

## Task 4: Update & Delete Practice
```sql
UPDATE Employees SET Salary = Salary * 1.1 WHERE DeptID = 1;
DELETE FROM Employees WHERE EmpID = 2;
```
Verify changes with a `SELECT * FROM Employees;` before and after.

## Results
| Item | Value |
|---|---|
| Tables created | |
| Rows inserted | |
| Above-average earners found | |
| Avg salary per department | |
| Update applied correctly (Y/N) | |

## Screenshots
```
![Tables Created](Screenshots/tables-created.png)
![Query Results](Screenshots/query-results.png)
```

## Lab Summary
Note which SQL concept felt least intuitive (JOINs vs subqueries vs aggregates) and why.
