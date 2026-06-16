# Day 02 - Web Basics (HTTP, HTTPS, DNS, Browser)

## Goal
Understand how data travels between a browser and a server — this is the foundation for web security, pentesting, and understanding attacks like MITM, DNS spoofing, and session hijacking.

---

## 1. HTTP (HyperText Transfer Protocol)
Protocol used to transfer web pages and data between client (browser) and server.

### Request/Response Cycle
Browser (Client)  →  Request  →  Server

Browser (Client)  ←  Response ←  Server

A request contains:
- Method (GET, POST, etc.)
- URL/path
- Headers (metadata like browser type, cookies)
- Body (optional, e.g. form data)

A response contains:
- Status code (200, 404, 500, etc.)
- Headers
- Body (HTML, JSON, etc.)

### HTTP Methods
- **GET** — retrieve data (e.g., loading a page)
- **POST** — submit data (e.g., login form)
- **PUT** — update/replace a resource
- **DELETE** — remove a resource
- **PATCH** — partially update a resource

### Common Status Codes
| Code | Meaning |
|---|---|
| 200 | OK — success |
| 301 | Moved permanently (redirect) |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not found |
| 500 | Internal server error |

---

## 2. HTTPS (HTTP Secure)
HTTP encrypted using **TLS/SSL**.

Why it matters:
- Encrypts data in transit, so attackers on the network can't read it (prevents MITM/eavesdropping)
- Verifies the server's identity via certificates
- Padlock icon in browser = valid certificate trusted by browser's CA list

Key terms:
- **TLS handshake**: process where browser and server agree on encryption and verify identity before data transfer
- **Certificate**: issued by a trusted Certificate Authority (CA), proves the website's identity
- **Port**: HTTP uses port 80, HTTPS uses port 443

---

## 3. DNS (Domain Name System)
Translates human-readable domain names (e.g., google.com) into IP addresses computers use to communicate.

### Resolution Process
You type: google.com

↓

Browser checks local cache

↓

Asks DNS Resolver (usually your ISP or 8.8.8.8)

↓

Resolver queries Root → TLD (.com) → Authoritative DNS server

↓

Returns IP address (e.g., 142.250.X.X)

↓

Browser connects to that IP

### Common DNS Record Types
| Record | Purpose |
|---|---|
| A | Maps domain to IPv4 address |
| AAAA | Maps domain to IPv6 address |
| CNAME | Alias — points one domain to another |
| MX | Mail server records |
| TXT | Text data (often used for verification, SPF) |
| NS | Nameserver records for the domain |

### DNS Lookup Commands
nslookup google.com

dig google.com

---

## 4. Browser

### Rendering Engine Basics
Browser converts HTML/CSS/JS into the visual page:
1. Parses HTML → builds DOM (Document Object Model)
2. Parses CSS → builds CSSOM
3. Combines into render tree
4. Paints pixels on screen
5. JavaScript can modify DOM/CSSOM dynamically

### Developer Tools
Open with `F12` or `Ctrl+Shift+I`:
- **Elements tab** — inspect/edit live HTML/CSS
- **Console tab** — view JS errors, run JS commands
- **Network tab** — see every request/response, headers, timing, status codes (very useful for security analysis)
- **Application tab** — view cookies, local storage, session storage

---

## Interview Questions

**Q1. What is the difference between HTTP and HTTPS?**
HTTPS is HTTP encrypted with TLS/SSL, protecting data in transit and verifying server identity. HTTP sends data in plaintext.

**Q2. What happens when you type a URL into a browser?**
Browser checks cache → DNS resolves domain to IP → TCP connection established → TLS handshake (if HTTPS) → HTTP request sent → server responds → browser renders the page.

**Q3. What is DNS and why is it needed?**
DNS translates domain names into IP addresses, since computers communicate using IPs, not human-readable names.

**Q4. Difference between GET and POST?**
GET retrieves data and appends parameters to the URL (visible, cacheable). POST sends data in the request body (not visible in URL, used for sensitive/form data).

**Q5. What port does HTTPS use?**
Port 443. HTTP uses port 80.

**Q6. What is a CNAME record?**
A DNS record that aliases one domain name to another.

---



# Day 02 - Web Basics (HTTP, HTTPS, DNS, Browser)

## Introduction

The web allows users to access websites and services over the internet. Understanding how browsers, DNS, HTTP, and HTTPS work is fundamental for networking, cybersecurity, cloud computing, and web application security.

---

# HTTP (HyperText Transfer Protocol)

HTTP is the protocol used for communication between a browser (client) and a web server.

Example:

Browser → Request → Server

Server → Response → Browser

## HTTP Request Methods

### GET

Used to retrieve data.

Example:

GET /index.html

### POST

Used to send data to a server.

Example:

POST /login

### PUT

Used to update existing data.

### DELETE

Used to delete data.

---

# HTTP Status Codes

## 200 OK

Request successful.

## 301 Moved Permanently

Resource moved to another location.

## 404 Not Found

Requested page does not exist.

## 500 Internal Server Error

Server encountered an error.

---

# HTTPS (HyperText Transfer Protocol Secure)

HTTPS is the secure version of HTTP.

HTTPS uses:

* SSL
* TLS
* Digital Certificates

Benefits:

* Encryption
* Integrity
* Authentication

Example:

http://example.com

https://example.com

---

# DNS (Domain Name System)

DNS converts domain names into IP addresses.

Example:

google.com

↓

142.250.x.x

Without DNS, users would need to remember IP addresses.

---

# Common DNS Records

## A Record

Maps a domain to an IPv4 address.

## AAAA Record

Maps a domain to an IPv6 address.

## CNAME Record

Creates an alias for another domain.

## MX Record

Used for email routing.

## TXT Record

Stores text information such as SPF records.

---

# DNS Resolution Process

1. User enters google.com
2. Browser checks cache
3. OS checks DNS cache
4. Query sent to DNS resolver
5. Resolver contacts DNS servers
6. IP address returned
7. Browser connects to server

---

# Browser Basics

Popular Browsers:

* Google Chrome
* Mozilla Firefox
* Microsoft Edge
* Brave

---

# Cookies

Cookies store user information.

Examples:

* Login session
* Preferences
* Shopping cart data

---

# Sessions

Sessions maintain user state while browsing.

Example:

Login once and continue accessing pages without logging in again.

---

# Cache

Browsers cache files for faster loading.

Benefits:

* Faster websites
* Reduced bandwidth usage

---

# Browser Developer Tools

Open Developer Tools:

F12

Useful Tabs:

* Elements
* Console
* Network
* Application
* Security

---

# What Happens When You Visit a Website

1. Enter URL
2. Browser checks cache
3. DNS lookup
4. TCP connection established
5. TLS handshake (HTTPS)
6. HTTP request sent
7. Server processes request
8. HTTP response received
9. Browser renders page

---

# Interview Questions

1. What is HTTP?
2. Difference between HTTP and HTTPS?
3. What is DNS?
4. What is an A Record?
5. What is a Cookie?
6. What is a Session?
7. What does a 404 error mean?
8. What is TLS?
9. What is browser cache?
10. Explain DNS resolution process.


## Key Takeaways
- Understood the HTTP request/response cycle and common methods/status codes
- Learned how HTTPS secures HTTP using TLS and certificates
- Understood the full DNS resolution process and major record types
- Learned how browsers render pages and how to use DevTools for inspection
