# Day 17 - Networking Fundamentals

## Goal
Build foundational networking knowledge - the OSI/TCP-IP models, IP addressing, and ports - essential before subnetting, routing, and CCNA topics.

---

## 1. OSI Model (7 Layers)

A conceptual framework describing how data moves through a network, layer by layer.

```
7. Application   - HTTP, FTP, DNS, SMTP (user-facing protocols)
6. Presentation  - Encryption, compression, data formatting (SSL/TLS)
5. Session       - Session establishment/management
4. Transport     - TCP, UDP (end-to-end delivery, ports)
3. Network       - IP, routing (logical addressing)
2. Data Link     - MAC addresses, switches (physical addressing)
1. Physical      - Cables, electrical signals, hardware
```

Mnemonic: "All People Seem To Need Data Processing" (Application down to Physical)

## 2. TCP/IP Model

A simplified, practically-used 4-layer model (what the real internet is built on):
```
4. Application   (combines OSI layers 5-7)
3. Transport      (TCP/UDP)
2. Internet         (IP)
1. Network Access     (combines OSI layers 1-2)
```

## 3. IP Addressing (IPv4/IPv6)

### IPv4
32-bit address, written as 4 octets: `192.168.1.1`
Each octet: 0-255 (8 bits each)

Address classes (historical, less relevant with CIDR now but still asked in interviews):
```
Class A: 1.0.0.0 - 126.255.255.255   (large networks)
Class B: 128.0.0.0 - 191.255.255.255  (medium networks)
Class C: 192.0.0.0 - 223.255.255.255   (small networks)
```

Private IP ranges (non-internet-routable):
```
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
```

### IPv6
128-bit address, written in hexadecimal: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
Designed to solve IPv4 address exhaustion - vastly larger address space.

## 4. Ports & Sockets

A **port** identifies a specific process/service on a device (0-65535).

Common ports to memorize:
| Port | Service |
|---|---|
| 20/21 | FTP |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3389 | RDP |
| 3306 | MySQL |
| 5432 | PostgreSQL |

A **socket** = IP address + Port, uniquely identifying a connection endpoint (e.g., `192.168.1.10:443`).

---

## Interview Questions

**Q1. Name the 7 layers of the OSI model in order.**
Physical, Data Link, Network, Transport, Session, Presentation, Application.

**Q2. What layer does IP operate at? What about TCP?**
IP operates at the Network layer (Layer 3); TCP operates at the Transport layer (Layer 4).

**Q3. What is a socket?**
The combination of an IP address and a port number, uniquely identifying a network connection endpoint.

**Q4. What port does HTTPS use, and what layer handles encryption in the OSI model?**
Port 443; encryption (TLS/SSL) is associated with the Presentation layer (Layer 6), though TLS in practice operates between Transport and Application layers.

## Key Takeaways
- Learned the OSI model's 7 layers and their purposes
- Learned the simplified TCP/IP 4-layer model
- Learned IPv4 addressing, classes, and private ranges
- Learned IPv6 basics and why it exists
- Learned ports, common service-port mappings, and the socket concept
