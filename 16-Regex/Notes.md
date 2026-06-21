# Day 16 - Regular Expressions (Regex)

## Goal
Learn pattern matching for text - essential for log parsing, input validation, and threat hunting throughout the rest of this roadmap.

---

## 1. Basic Patterns & Metacharacters

| Pattern | Meaning |
|---|---|
| `.` | any single character |
| `^` | start of string |
| `$` | end of string |
| `\d` | any digit (0-9) |
| `\w` | any word character (letters, digits, underscore) |
| `\s` | any whitespace |
| `[abc]` | any one of a, b, or c |
| `[^abc]` | any character EXCEPT a, b, c |
| `[a-z]` | any lowercase letter (range) |

Example:
```python
import re
re.search(r'^Hello', "Hello World")     # matches, starts with Hello
re.search(r'World$', "Hello World")      # matches, ends with World
re.search(r'\d+', "Order 12345")          # matches "12345"
```

## 2. Quantifiers & Anchors

| Quantifier | Meaning |
|---|---|
| `*` | 0 or more |
| `+` | 1 or more |
| `?` | 0 or 1 (optional) |
| `{n}` | exactly n times |
| `{n,m}` | between n and m times |

Example - matching an IP address:
```python
ip_pattern = r'\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}'
re.search(ip_pattern, "Connection from 192.168.1.100")
```

## 3. Groups & Lookarounds

**Groups** `()` capture parts of a match for extraction.
```python
match = re.search(r'(\d{4})-(\d{2})-(\d{2})', "Date: 2026-06-21")
if match:
    year, month, day = match.groups()
    print(year, month, day)   # 2026 06 21
```

**Lookarounds** match based on surrounding context without consuming it.
```python
# Positive lookahead: match "user" only if followed by "=admin"
re.search(r'user(?==admin)', "user=admin")

# Negative lookahead: match "user" only if NOT followed by "=admin"
re.search(r'user(?!=admin)', "user=guest")
```

## 4. Use Cases (Log Parsing, Validation)

### Email Validation
```python
email_pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'
re.match(email_pattern, "user@example.com")
```

### Extracting IPs from a Log File
```python
import re

with open("access.log") as f:
    for line in f:
        ips = re.findall(r'\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b', line)
        for ip in ips:
            print(ip)
```

### Detecting Suspicious Patterns (Security Context)
```python
# Detect potential SQL injection attempts in logs
sqli_pattern = r"(\bUNION\b|\bSELECT\b.*\bFROM\b|--|;--|\bOR\b\s+1=1)"
re.search(sqli_pattern, log_line, re.IGNORECASE)
```

---

## Interview Questions

**Q1. What's the difference between `*` and `+` quantifiers?**
`*` matches 0 or more occurrences; `+` matches 1 or more (requires at least one).

**Q2. What does `\d{1,3}` match?**
Between 1 and 3 digits.

**Q3. What is a capturing group used for?**
Extracting specific portions of a regex match, accessible via `.group()` or `.groups()`.

**Q4. Why is regex useful in security work?**
It enables fast pattern-based detection in logs - extracting IPs, detecting attack signatures (like SQLi patterns), and validating input.

## Key Takeaways
- Learned core regex metacharacters and patterns
- Learned quantifiers and anchors
- Learned capturing groups and lookaround basics
- Applied regex to practical use cases: IP extraction, email validation, security pattern detection
