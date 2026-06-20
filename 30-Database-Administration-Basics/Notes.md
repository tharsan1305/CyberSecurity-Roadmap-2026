# Day 30 - Database Administration Basics

## Goal
Learn core DBA responsibilities - backup/restore, performance tuning, user management - essential for keeping databases available, performant, and secure.

---

## 1. Backup & Restore

Databases need regular backups to prevent data loss from hardware failure, corruption, or accidental deletion.

Backup types:
- **Full Backup**: complete copy of the entire database
- **Incremental Backup**: only changes since the last backup (faster, smaller)
- **Differential Backup**: changes since the last FULL backup (middle ground)

MySQL backup/restore example:
```bash
mysqldump -u root -p database_name > backup.sql
mysql -u root -p database_name < backup.sql
```

PostgreSQL backup/restore example:
```bash
pg_dump database_name > backup.sql
psql database_name < backup.sql
```

## 2. Indexing & Performance Tuning

An **index** is a data structure that speeds up data retrieval at the cost of additional storage and slower writes.

```sql
CREATE INDEX idx_employee_name ON Employees(Name);
```

Without an index, the database performs a full table scan (checking every row) - slow on large tables. With an index, lookups become much faster (similar to a book's index vs reading every page).

Trade-off: indexes speed up SELECT queries but slow down INSERT/UPDATE/DELETE (since the index must also be updated).

Performance tuning basics:
- Add indexes on frequently filtered/joined columns
- Avoid `SELECT *` when only specific columns are needed
- Use `EXPLAIN` to analyze query execution plans

```sql
EXPLAIN SELECT * FROM Employees WHERE Name = 'Tharsan';
```

## 3. User Roles & Privileges

DBAs control who can access/modify what within a database.

```sql
CREATE USER 'analyst'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT ON database_name.* TO 'analyst'@'localhost';
REVOKE SELECT ON database_name.* FROM 'analyst'@'localhost';
```

Principle of least privilege applies here too - a reporting/analyst account should only have SELECT, never DELETE or DROP.

## 4. Replication Basics

Replication copies data from one database (primary/master) to one or more others (replica/slave) for redundancy, read scaling, or disaster recovery.

- **Master-Slave Replication**: writes go to master, reads can be distributed across replicas
- **Master-Master Replication**: multiple nodes can accept writes, more complex conflict handling

---

## Interview Questions

**Q1. Difference between Full, Incremental, and Differential backups?**
Full backs up everything; Incremental backs up only changes since the last backup (any type); Differential backs up changes since the last Full backup.

**Q2. What is an index and what's the trade-off of using one?**
A data structure that speeds up data retrieval; the trade-off is increased storage use and slower write operations (INSERT/UPDATE/DELETE).

**Q3. Why is least privilege important for database user accounts?**
It limits damage from compromised credentials or accidental mistakes by ensuring accounts only have the access they actually need.

**Q4. What is database replication used for?**
Redundancy, disaster recovery, and distributing read load across multiple database copies.

## Key Takeaways
- Learned backup types and how to perform backup/restore in MySQL/PostgreSQL
- Understood indexing and its performance trade-offs
- Learned user privilege management and least privilege principle
- Understood basic replication concepts (master-slave, master-master)
