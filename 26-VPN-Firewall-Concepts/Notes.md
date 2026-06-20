# Day 26 - VPN & Firewall Concepts

## Goal
Understand how VPNs secure remote connectivity and how NAT/firewall policies control traffic flow - critical for both networking and security roles.

---

## 1. VPN Types

### Site-to-Site VPN
Connects two entire networks (e.g., a branch office to headquarters) over the internet, encrypting all traffic between the two sites. Configured between gateway devices (routers/firewalls), transparent to end users.

### Remote Access VPN
Connects an individual user's device to a private network remotely (e.g., an employee working from home connecting to the company network). Requires client software (e.g., Cisco AnyConnect, OpenVPN client, WireGuard).

## 2. IPSec & SSL VPN

### IPSec (Internet Protocol Security)
A suite of protocols that authenticates and encrypts IP packets. Operates at the network layer, commonly used for site-to-site VPNs.

Two main modes:
- **Tunnel mode**: encrypts the entire IP packet, used for site-to-site VPNs
- **Transport mode**: encrypts only the payload, typically used for host-to-host communication

Key components: IKE (Internet Key Exchange) for negotiating security associations, ESP (Encapsulating Security Payload) for encryption.

### SSL VPN
Uses SSL/TLS (same technology securing HTTPS) to create a secure tunnel, often via a web browser - simpler for remote access VPNs since no special client may be needed (clientless SSL VPN) or a lightweight client is used.

| | IPSec VPN | SSL VPN |
|---|---|---|
| Layer | Network layer | Application/Transport layer |
| Typical use | Site-to-site | Remote access |
| Client needed | Usually yes | Often clientless (browser-based) |

## 3. Firewall Rules & Policies

Firewall policies define what traffic is allowed/denied, typically structured as an ordered rule list evaluated top-down, with an implicit "deny all" at the end.

Best practice: **principle of least privilege** - only allow the specific traffic required, deny everything else by default.

## 4. NAT (Network Address Translation)

Translates private IP addresses (internal network) to a public IP address (internet-facing) and vice versa - allows multiple internal devices to share one public IP.

Types:
- **Static NAT**: one-to-one mapping between a private and public IP, permanent
- **Dynamic NAT**: maps private IPs to a pool of public IPs, assigned on demand
- **PAT (Port Address Translation / NAT Overload)**: maps many private IPs to one public IP using different port numbers - most common in home/office routers

Example PAT flow:
```
Internal: 192.168.1.10:5000  →  NAT  →  Public: 203.0.113.5:40001
Internal: 192.168.1.11:5000  →  NAT  →  Public: 203.0.113.5:40002
```

---

## Interview Questions

**Q1. Difference between Site-to-Site and Remote Access VPN?**
Site-to-Site connects two entire networks together (office to office); Remote Access VPN connects an individual user's device to a private network.

**Q2. Difference between IPSec and SSL VPN?**
IPSec operates at the network layer and is commonly used for site-to-site VPNs; SSL VPN operates at the application/transport layer using TLS, often browser-based for remote access.

**Q3. What is NAT used for?**
Translating private internal IP addresses to a public IP (and back), allowing internal devices to access the internet while conserving public IP addresses.

**Q4. What is PAT?**
Port Address Translation - maps multiple private IPs to a single public IP by tracking unique port numbers per connection; the most common form of NAT used in home/office routers.

## Key Takeaways
- Understood Site-to-Site vs Remote Access VPN use cases
- Learned IPSec (tunnel/transport mode) vs SSL VPN differences
- Understood firewall rule structure and least-privilege principle
- Learned NAT types: Static, Dynamic, PAT
