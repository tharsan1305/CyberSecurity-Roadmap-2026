# Day 30 - Lab: Database Administration

## Objective
Practice backup/restore, indexing, and user privilege management.

## Task 1: Backup and Restore (using library DB from Day 28)
```bash
mysqldump -u root -p library > library_backup.sql
mysql -u root -p -e "DROP DATABASE library;"
mysql -u root -p -e "CREATE DATABASE library;"
mysql -u root -p library < library_backup.sql
```
Verify data is restored: `SELECT * FROM Books;`

## Task 2: Add an Index and Compare Performance
```sql
-- Before index
EXPLAIN SELECT * FROM Employees WHERE Name = 'Tharsan';

CREATE INDEX idx_name ON Employees(Name);

-- After index
EXPLAIN SELECT * FROM Employees WHERE Name = 'Tharsan';
```
Record: difference in the EXPLAIN output (look for "type" and "key" columns).

## Task 3: Create a Restricted User
```sql
CREATE USER 'readonly_user'@'localhost' IDENTIFIED BY 'SecurePass123';
GRANT SELECT ON library.* TO 'readonly_user'@'localhost';
FLUSH PRIVILEGES;
```
Test: log in as `readonly_user` and attempt a SELECT (should work) and a DELETE (should fail).

## Results
| Item | Value |
|---|---|
| Backup file created (Y/N) | |
| Restore successful (Y/N) | |
| Index created (Y/N) | |
| EXPLAIN output changed (Y/N) | |
| Restricted user blocked from DELETE (Y/N) | |

## Screenshots
```
![Backup File](Screenshots/backup-file.png)
![Explain Before After](Screenshots/explain-comparison.png)
![Restricted User Test](Screenshots/restricted-user.png)
```

## Lab Summary
Note the EXPLAIN output difference before/after indexing, and confirm the restricted user truly couldn't perform unauthorized actions.
