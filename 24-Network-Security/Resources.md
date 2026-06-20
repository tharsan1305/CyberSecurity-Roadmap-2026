# Day 24 - Resources

## Tools Used
- Windows Firewall (`netsh advfirewall`)
- Cisco Packet Tracer (ACL labs)
- `arp` command (ARP table inspection)
- Snort/Suricata (reference, open-source IDS/IPS)

## Commands Reference
| Purpose | Command |
|---|---|
| View ARP table | `arp -a` |
| Show all firewall rules (Windows) | `netsh advfirewall firewall show rule name=all` |
| Cisco extended ACL deny | `access-list 101 deny tcp <src> <dst> eq <port>` |
| Apply ACL to interface | `ip access-group <acl-number> in/out` |

## Key Terms Glossary
- **NGFW**: Next-Generation Firewall, combines traditional filtering with deep packet inspection and app awareness
- **Signature-based detection**: matches known attack patterns
- **Anomaly-based detection**: flags deviation from a normal traffic baseline
- **ARP**: Address Resolution Protocol, maps IP addresses to MAC addresses on a LAN

## Further Reading
- Cisco Networking Academy: ACL configuration guides
- Snort.org documentation (open-source IDS/IPS)
- OWASP: Network attack fundamentals

## Skills Gained Today
- Firewall rule structure and types
- IDS vs IPS distinction and detection methods
- Cisco ACL configuration (standard/extended)
- Awareness of MITM, ARP spoofing, DNS spoofing, DoS/DDoS attack mechanics
