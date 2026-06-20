# Day 31 - Resources

## Tools Used
- Python `sqlite3` module (safe local SQLi demonstration)
- MySQL (SSL-enforced user configuration)

## Commands Reference
| Purpose | Code/Command |
|---|---|
| Vulnerable query pattern | `f"SELECT * FROM users WHERE username = '{input}'"` |
| Parameterized query (Python/sqlite3) | `cur.execute("SELECT * FROM users WHERE username = ?", (input,))` |
| Parameterized query (MySQL connector) | `cursor.execute("... WHERE username = %s", (input,))` |
| Require SSL for user | `CREATE USER ... REQUIRE SSL;` |
| Enable query logging (MySQL) | `SET GLOBAL general_log = 'ON';` |

## Key Terms Glossary
- **SQL Injection (SQLi)**: attack technique inserting malicious SQL via user input
- **Parameterized Query / Prepared Statement**: query execution method that separates code from data, preventing injection
- **RBAC**: Role-Based Access Control
- **Encryption at Rest**: protecting stored data on disk
- **Encryption in Transit**: protecting data moving across a network

## Further Reading
- OWASP SQL Injection Prevention Cheat Sheet (cheatsheetseries.owasp.org)
- PortSwigger Web Security Academy: SQL Injection (free, hands-on labs - relevant again in Web Pentesting phase)

## Skills Gained Today
- Practical understanding of SQL Injection mechanics
- Parameterized query implementation
- SSL-enforced database user configuration
- Database audit logging basics
