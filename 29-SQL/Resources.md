# Day 29 - Resources

## Tools Used
- MySQL / PostgreSQL
- DB Fiddle or SQLite Online (browser-based SQL sandboxes, no install needed)

## Commands Reference
| Purpose | SQL |
|---|---|
| Create table | `CREATE TABLE name (...);` |
| Insert row | `INSERT INTO table VALUES (...);` |
| Update row | `UPDATE table SET col=val WHERE condition;` |
| Delete row | `DELETE FROM table WHERE condition;` |
| Select with filter | `SELECT * FROM table WHERE condition;` |
| Inner join | `... INNER JOIN table2 ON a.id = b.id` |
| Group with aggregate | `SELECT col, COUNT(*) FROM table GROUP BY col;` |
| Filter groups | `... GROUP BY col HAVING condition` |

## Key Terms Glossary
- **DDL**: Data Definition Language (CREATE, ALTER, DROP)
- **DML**: Data Manipulation Language (INSERT, UPDATE, DELETE)
- **DQL**: Data Query Language (SELECT)
- **Aggregate Function**: a function that operates on multiple rows to return a single value (COUNT, SUM, AVG, MIN, MAX)

## Further Reading
- W3Schools SQL tutorial (w3schools.com/sql)
- Mode Analytics SQL tutorial (free, practical query examples)
- PostgreSQL/MySQL official documentation

## Skills Gained Today
- DDL/DML/DQL command fluency
- JOIN types and when to use each
- Subquery construction
- Aggregate functions with GROUP BY/HAVING
