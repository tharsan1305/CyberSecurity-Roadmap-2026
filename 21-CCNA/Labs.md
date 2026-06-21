# Day 21 - Lab: CCNA Comprehensive Practice

## Objective
Combine routing, switching, VLANs, and troubleshooting into one comprehensive Packet Tracer lab simulating a small CCNA-style exam scenario.

## Task 1: Build a Multi-Router Topology
- 2 Routers (R1, R2) connected via a serial or Ethernet WAN link
- 1 Switch connected to R1 with 2 VLANs (as in Topic 20)
- PCs in each VLAN

## Task 2: Configure Basic Device Settings
```
hostname R1
enable secret cisco123
line console 0
 password cisco
 login
line vty 0 4
 password cisco
 login
service password-encryption
```

## Task 3: Configure OSPF Between R1 and R2
```
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 10.0.0.0 0.0.0.3 area 0
```
Verify:
```
show ip ospf neighbor
show ip route
```

## Task 4: Verify End-to-End Connectivity
Ping from a PC on R1's VLAN to a PC/network reachable through R2. If it fails, troubleshoot using the OSI-based methodology from the Notes.

## Task 5: Save Configuration
```
copy running-config startup-config
```

## Results
| Item | Value |
|---|---|
| OSPF neighbor formed (Y/N) | |
| show ip route output (summary) | |
| End-to-end ping successful (Y/N) | |
| Config saved (Y/N) | |

## Screenshots
```
![Full Topology](Screenshots/full-topology.png)
![OSPF Neighbors](Screenshots/ospf-neighbors.png)
![End to End Ping](Screenshots/e2e-ping.png)
```

## Lab Summary
Note any troubleshooting you had to do to get the OSPF neighbor relationship to form, and what the most common misconfiguration was (often: mismatched network statements or wildcard masks).
