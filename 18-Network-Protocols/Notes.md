# Day 18 - Network Protocols (TCP/IP, UDP, ICMP)

## Goal
Understand the core transport-layer protocols and key application protocols that run on top of them.

---

## 1. TCP - Connection-Oriented, Handshake

TCP (Transmission Control Protocol) guarantees reliable, ordered delivery of data.

**Three-Way Handshake** (connection establishment):
```
Client -> SYN -> Server
Client <- SYN-ACK <- Server
Client -> ACK -> Server
(Connection established)
```

**Four-Way Handshake** (connection termination):
```
Client -> FIN -> Server
Client <- ACK <- Server
Client <- FIN <- Server
Client -> ACK -> Server
```

TCP features: reliability (retransmits lost packets), ordering (sequence numbers), flow control, error checking.

Use cases: web browsing (HTTP/HTTPS), email (SMTP), file transfer (FTP) - anywhere data integrity matters more than speed.

## 2. UDP - Connectionless, Fast Transfer

UDP (User Datagram Protocol) sends data without establishing a connection or guaranteeing delivery - "fire and forget."

Characteristics: no handshake, no retransmission, no ordering guarantee, much lower overhead than TCP.

Use cases: DNS queries, video streaming, VoIP, online gaming - where speed matters more than guaranteed delivery (a dropped video frame is less harmful than the delay of waiting for retransmission).

| | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | No guarantee |
| Speed | Slower (overhead) | Faster |
| Use case | Web, email, file transfer | DNS, streaming, gaming |

## 3. ICMP - Ping, Traceroute, Error Messages

ICMP (Internet Control Message Protocol) is used for network diagnostics and error reporting, not for transferring application data.

```bash
ping 8.8.8.8        # uses ICMP Echo Request/Reply
traceroute 8.8.8.8     # uses ICMP (or UDP) with increasing TTL to map the path
```

How traceroute works (simplified): sends packets with increasing TTL (Time To Live) values; each router that drops a TTL-expired packet sends back an ICMP "Time Exceeded" message, revealing each hop along the path.

Security note: ICMP can be abused for reconnaissance (ping sweeps) or certain DoS techniques (ICMP flood), which is why many firewalls restrict/rate-limit it.

## 4. Common Protocols (HTTP, FTP, SSH, DNS)

| Protocol | Port | Transport | Purpose |
|---|---|---|---|
| HTTP | 80 | TCP | Web browsing |
| HTTPS | 443 | TCP | Secure web browsing |
| FTP | 20/21 | TCP | File transfer |
| SSH | 22 | TCP | Secure remote access |
| DNS | 53 | UDP (mostly), TCP for large responses | Domain name resolution |
| SMTP | 25 | TCP | Sending email |

---

## Interview Questions

**Q1. Explain the TCP three-way handshake.**
SYN (client requests connection) -> SYN-ACK (server acknowledges and responds) -> ACK (client confirms) - establishing a reliable connection before data transfer.

**Q2. Why does DNS typically use UDP instead of TCP?**
DNS queries are small and speed-sensitive; UDP's lower overhead makes lookups faster. TCP is used as a fallback for larger DNS responses (e.g., zone transfers).

**Q3. What does ICMP do, and is it used for normal application data?**
It's used for network diagnostics and error reporting (like ping and traceroute), not for carrying application data like web pages or files.

**Q4. Why might a firewall block or rate-limit ICMP?**
To prevent reconnaissance techniques like ping sweeps and to mitigate ICMP flood-based denial-of-service attacks.

## Key Takeaways
- Learned TCP's three-way/four-way handshake and reliability features
- Learned UDP's connectionless, low-overhead model and its use cases
- Learned ICMP's role in diagnostics (ping, traceroute) and security implications
- Learned common application protocols and their default ports/transport layers
