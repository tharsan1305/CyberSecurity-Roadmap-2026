# Day 24 - Network Security

## Goal
Understand how networks are defended - firewalls, IDS/IPS, ACLs, and common network-layer attacks. This is foundational for both defensive (SOC) and offensive (pentesting) security work later in the roadmap.

---

## 1. Firewalls

A firewall controls traffic in/out of a network based on rules.

Types:
- **Packet-filtering firewall**: inspects packet headers (IP, port) only, fast but limited
- **Stateful firewall**: tracks connection state (established, related), more intelligent than packet-filtering
- **Next-Generation Firewall (NGFW)**: adds application-layer awareness, intrusion prevention, deep packet inspection

Rule components typically include: source IP, destination IP, port, protocol, action (allow/deny).

Example rule logic:
```
Allow: Source=Any, Dest=192.168.1.10, Port=443, Protocol=TCP
Deny: Source=Any, Dest=Any, Port=Any (implicit deny-all at the end)
```

## 2. IDS/IPS

- **IDS (Intrusion Detection System)**: monitors traffic, alerts on suspicious activity, does NOT block
- **IPS (Intrusion Prevention System)**: monitors traffic AND actively blocks/drops malicious traffic in real time

Detection methods:
- **Signature-based**: matches known attack patterns (fast, but misses novel attacks)
- **Anomaly-based**: flags deviations from a baseline of normal behavior (catches novel attacks, more false positives)

Common tools: Snort, Suricata (open-source IDS/IPS)

## 3. ACLs (Access Control Lists)

Rules applied on routers/switches to permit or deny traffic based on criteria (source/destination IP, port, protocol).

Cisco ACL example:
```
access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 443
access-list 101 deny ip any any
```

Types:
- **Standard ACL**: filters based on source IP only
- **Extended ACL**: filters based on source/destination IP, port, protocol - more granular

## 4. Common Network Attacks

### MITM (Man-in-the-Middle)
Attacker intercepts communication between two parties without their knowledge, potentially reading/modifying traffic.

### ARP Spoofing
Attacker sends forged ARP (Address Resolution Protocol) replies to associate their MAC address with another device's IP (often the gateway), redirecting traffic through the attacker - a common technique to enable MITM on a LAN.

### Other common attacks
- **DNS Spoofing**: forging DNS responses to redirect victims to malicious sites
- **DoS/DDoS**: flooding a target with traffic to exhaust resources and deny legitimate access
- **Port Scanning**: reconnaissance technique to discover open ports/services (covered more in Pentesting phase)

---

## Interview Questions

**Q1. Difference between IDS and IPS?**
IDS only detects and alerts on suspicious traffic; IPS detects AND actively blocks malicious traffic in real time.

**Q2. What is a stateful firewall?**
A firewall that tracks the state of active connections, allowing return traffic for established sessions rather than evaluating every packet independently.

**Q3. What is ARP spoofing used for?**
Associating the attacker's MAC address with a legitimate IP (often the gateway) to intercept or redirect traffic on a local network - typically a precursor to a MITM attack.

**Q4. Standard vs Extended ACL?**
Standard ACLs filter based on source IP only; Extended ACLs filter based on source/destination IP, port, and protocol for more granular control.

## Key Takeaways
- Learned firewall types and how rules are structured
- Understood the difference between IDS and IPS and their detection methods
- Learned ACL types and Cisco ACL syntax
- Understood common network attacks: MITM, ARP spoofing, DNS spoofing, DoS/DDoS
