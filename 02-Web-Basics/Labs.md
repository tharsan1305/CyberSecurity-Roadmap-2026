# Day 02 - Lab: HTTP, DNS & Browser Inspection

## Objective
Practice inspecting HTTP requests/responses, performing DNS lookups, and using browser DevTools.

---

## Task 1: DNS Lookup
nslookup google.com

dig google.com

Record:
- IP address returned
- Any CNAME records found
- Time taken (if shown)

---

## Task 2: Inspect HTTP Headers with curl
curl -I https://www.google.com

Record:
- Status code returned
- Server header (if shown)
- Content-Type header

---

## Task 3: Browser DevTools — Network Tab

1. Open any website
2. Press `F12` → go to **Network** tab
3. Reload the page
4. Click on the first request (usually the HTML document)

Record:
- Request method (GET/POST)
- Status code
- Response headers (at least 3)
- Total load time

---

## Task 4: Check HTTPS Certificate

1. Visit any HTTPS site
2. Click the padlock icon in the address bar
3. View certificate details

Record:
- Issued to (domain)
- Issued by (CA name)
- Valid from / valid until dates

---

## Results

| Item | Value |
|---|---|
| DNS IP for google.com | |
| CNAME (if any) | |
| curl status code | |
| Server header | |
| Network tab status code | |
| Certificate issued by | |
| Certificate valid until | |

---

## Screenshots
Save in `Screenshots/` subfolder:
