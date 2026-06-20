# Day 24 - Lab: Network Security

## Objective
Practice configuring ACLs, inspecting firewall rules, and understanding ARP behavior.

## Task 1: Windows Firewall Rule Inspection
```
netsh advfirewall firewall show rule name=all | more
```
Record: count of inbound vs outbound rules visible.

## Task 2: View ARP Table
```
arp -a          (Windows/Linux)
```
Record: your gateway's MAC address and IP as shown.

## Task 3: Cisco Packet Tracer - ACL Configuration
1. Build a simple topology: 2 PCs, 1 router, 1 switch
2. Configure an extended ACL on the router to block one PC from reaching the other on a specific port (e.g., block Telnet/port 23)
3. Verify with a ping/telnet test from the blocked PC

Example commands:
```
access-list 101 deny tcp host 192.168.1.10 host 192.168.1.20 eq 23
access-list 101 permit ip any any
interface gig0/0
 ip access-group 101 in
```

## Task 4: Simulate ARP Spoofing Awareness (Conceptual/Lab Environment Only)
In an isolated lab (e.g., a VM lab network you own, never on shared/production networks), explore how `arpwatch` or similar tools detect ARP table changes. This is observation only at this stage - active ARP spoofing techniques are covered properly in the Network Pentesting phase (Topic 63) with explicit lab permission scope.

## Results
| Item | Value |
|---|---|
| Inbound firewall rules count | |
| Gateway MAC address | |
| ACL blocked traffic successfully (Y/N) | |
| ARP table entries observed | |

## Screenshots
```
![Firewall Rules](Screenshots/firewall-rules.png)
![ARP Table](Screenshots/arp-table.png)
![Packet Tracer ACL Test](Screenshots/acl-test.png)
```

## Lab Summary
Note what the ACL blocked successfully, and any unexpected behavior you observed.
