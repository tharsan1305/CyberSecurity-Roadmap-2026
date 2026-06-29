# Day 58 - Lab: OWASP Top 10

## Objective
Practice identifying OWASP Top 10 vulnerabilities using a legal, intentionally vulnerable application.

## Task 1: Set Up OWASP Juice Shop
```bash
docker run -d -p 3000:3000 bkimminich/juice-shop
```
Access at `http://localhost:3000`

## Task 2: Find and Exploit a Reflected XSS
Explore the search functionality and attempt: `<script>alert('XSS')</script>` in a search field.

## Task 3: Find an IDOR
Log in as a normal user, find your own order/basket ID in the URL, then try modifying it to access another user's data.

## Task 4: Document Findings
For each finding, write: vulnerability type, steps to reproduce, and potential impact - this is real-world pentest report practice.

## Results
| Item | Value |
|---|---|
| Juice Shop running (Y/N) | |
| XSS triggered (Y/N) | |
| IDOR attempted (Y/N) | |
| Findings documented (Y/N) | |

## Lab Summary
Note which vulnerability felt easiest to find versus hardest, and why.
