# Day 30 - Resources

## Tools Used
- MySQL (`mysqldump`, `mysql` CLI)
- PostgreSQL (`pg_dump`, `psql`)

## Commands Reference
| Purpose | Command |
|---|---|
| Backup MySQL DB | `mysqldump -u root -p dbname > backup.sql` |
| Restore MySQL DB | `mysql -u root -p dbname < backup.sql` |
| Backup PostgreSQL DB | `pg_dump dbname > backup.sql` |
| Create index | `CREATE INDEX idx_name ON table(column);` |
| Analyze query plan | `EXPLAIN SELECT ...;` |
| Create user | `CREATE USER 'name'@'host' IDENTIFIED BY 'pass';` |
| Grant privilege | `GRANT SELECT ON db.* TO 'user'@'host';` |
| Revoke privilege | `REVOKE SELECT ON db.* FROM 'user'@'host';` |

## Key Terms Glossary
- **Full/Incremental/Differential Backup**: backup strategies balancing speed vs completeness
- **Index**: data structure improving read performance at the cost of write performance
- **Least Privilege**: granting only the minimum access necessary
- **Replication**: copying data across database instances for redundancy/scaling

## Further Reading
- MySQL official documentation: Backup and Recovery
- PostgreSQL official documentation: Backup and Restore
- Use The Index, Luke (use-the-index-luke.com) - free in-depth indexing resource

## Skills Gained Today
- Database backup and restore procedures
- Indexing and query performance analysis (EXPLAIN)
- User privilege management and least privilege enforcement
- Replication concepts (master-slave, master-master)
