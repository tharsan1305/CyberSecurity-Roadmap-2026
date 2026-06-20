# Day 31 - Database Security

## Goal
Learn how to protect databases from unauthorized access and attacks - directly connects to OWASP Top 10 (SQL Injection) covered later in the roadmap.

---

## 1. Access Control & Authentication

Layers of database access control:
- **Authentication**: verifying who is connecting (username/password, certificates, IAM-based auth in cloud DBs)
- **Authorization**: what the authenticated user is allowed to do (handled via GRANT/REVOKE, covered Day 30)

Best practices:
- Never use default credentials (e.g., default `root`/`admin` passwords)
- Enforce strong password policies
- Use role-based access control (RBAC) - group permissions into roles rather than assigning individually
- Restrict database network access (e.g., don't expose database ports directly to the internet)

## 2. Encryption (At Rest, In Transit)

**Encryption at Rest**: data is encrypted while stored on disk, protecting it if physical storage is stolen or accessed without authorization.
- MySQL: InnoDB tablespace encryption
- PostgreSQL: filesystem-level encryption (e.g., LUKS) or pgcrypto extension

**Encryption in Transit**: data is encrypted while moving between client and database server, preventing network eavesdropping.
- Enforced via SSL/TLS connections to the database

```sql
-- MySQL: require SSL for a user
ALTER USER 'analyst'@'%' REQUIRE SSL;
```

## 3. SQL Injection Prevention

**SQL Injection (SQLi)**: an attack where malicious SQL code is inserted into input fields, manipulating the query the application executes.

Vulnerable example (string concatenation):
```python
query = "SELECT * FROM users WHERE username = '" + user_input + "'"
```
If `user_input` is `' OR '1'='1`, the query becomes:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1'
```
This returns ALL users, bypassing intended logic.

**Prevention: Parameterized Queries (Prepared Statements)**
```python
cursor.execute("SELECT * FROM users WHERE username = %s", (user_input,))
```
The input is treated strictly as data, never as executable SQL code - this is the primary defense.

Additional prevention:
- Input validation/sanitization
- Least privilege database accounts (limit damage even if injection succeeds)
- Web Application Firewalls (WAF) as a secondary layer, not a replacement for proper code fixes

## 4. Auditing & Logging

Database auditing tracks who did what, when - critical for detecting unauthorized access and for compliance (covered later in Topic 82).

What to log:
- Login attempts (successful and failed)
- Schema changes (DDL operations)
- Sensitive data access (e.g., who queried a "Salaries" table)

MySQL example (enabling general query log for auditing, used cautiously due to performance/storage impact):
```sql
SET GLOBAL general_log = 'ON';
SET GLOBAL general_log_file = '/var/log/mysql/query.log';
```

---

## Interview Questions

**Q1. What is SQL Injection and how do you prevent it?**
An attack where malicious SQL is inserted via user input to manipulate a query. Prevented primarily through parameterized queries/prepared statements, never building queries via string concatenation.

**Q2. Difference between encryption at rest and in transit?**
At rest protects stored data on disk; in transit protects data moving across the network between client and server.

**Q3. Why use Role-Based Access Control (RBAC) instead of per-user permissions?**
It's easier to manage and audit at scale - permissions are assigned to roles, and users are assigned to roles, rather than managing individual grants per user.

**Q4. Why is database auditing important?**
It provides visibility into who accessed or modified data and when, essential for detecting breaches and meeting compliance requirements.

## Key Takeaways
- Learned authentication vs authorization in database security
- Understood encryption at rest vs in transit
- Learned SQL Injection mechanics and parameterized query prevention
- Understood database auditing/logging fundamentals
