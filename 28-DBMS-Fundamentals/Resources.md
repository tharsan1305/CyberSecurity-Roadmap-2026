# Day 28 - Resources

## Tools Used
- MySQL or PostgreSQL (RDBMS)
- Any ER diagram tool (draw.io, dbdiagram.io, or pen and paper)

## Commands Reference
| Purpose | SQL |
|---|---|
| Create database | `CREATE DATABASE dbname;` |
| Create table | `CREATE TABLE name (...);` |
| Define primary key | `id INT PRIMARY KEY` |
| Define foreign key | `FOREIGN KEY (col) REFERENCES table(col)` |
| Insert data | `INSERT INTO table (...) VALUES (...);` |
| Join tables | `SELECT ... FROM a JOIN b ON a.id = b.id;` |

## Key Terms Glossary
- **RDBMS**: Relational Database Management System
- **Entity**: a table representing a real-world object
- **Normalization**: process of reducing data redundancy via 1NF/2NF/3NF
- **Junction Table**: a table resolving many-to-many relationships into two one-to-many relationships
- **Atomic Value**: an indivisible single value in a column (required for 1NF)

## Further Reading
- dbdiagram.io (free ER diagram tool, useful going forward)
- W3Schools: SQL and Database Normalization guides
- PostgreSQL/MySQL official documentation

## Skills Gained Today
- ER diagram design
- Database normalization (1NF, 2NF, 3NF) applied practically
- Primary Key/Foreign Key schema design
- Basic JOIN query writing
