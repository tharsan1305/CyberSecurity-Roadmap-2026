# Day 02 - Resources

## Commands Reference

| Purpose | Command |
|---|---|
| DNS Lookup | `nslookup <domain>` |
| Detailed DNS Query | `dig <domain>` |
| HTTP Headers Only | `curl -I <url>` |
| Full HTTP Response | `curl <url>` |
| Verbose curl (full handshake) | `curl -v <url>` |

## Concepts Covered
- HTTP request/response cycle, methods, status codes
- HTTPS/TLS encryption and certificates
- DNS resolution process and record types (A, AAAA, CNAME, MX, TXT, NS)
- Browser rendering pipeline (DOM, CSSOM, render tree)
- Browser DevTools (Elements, Console, Network, Application tabs)

## Key Terms Glossary
- **DOM**: Document Object Model, browser's in-memory representation of HTML
- **TLS Handshake**: negotiation process to establish an encrypted connection
- **CA (Certificate Authority)**: trusted entity that issues SSL/TLS certificates
- **Resolver**: DNS server that performs lookups on behalf of the client
- **TTL (DNS)**: how long a DNS record is cached before re-querying

## Further Reading
- MDN Web Docs: HTTP overview
- Cloudflare Learning Center: What is DNS / What is TLS
- `man curl`, `man nslookup`, `man dig`

## Tools Used Today
- Browser DevTools (F12)
- `nslookup`, `dig`, `curl` (terminal)
