# Day 22 - Lab: Capstone Small Business Network

## Objective
Design and build a complete small-business network topology combining everything from Topics 17-21, then deliberately introduce and fix 3 faults.

## Task 1: Design Phase (Do This on Paper/Notes First)
Design a network for a small business with:
- Sales department (20 hosts)
- IT department (10 hosts)
- Server VLAN (5 hosts: file server, web server, etc.)
- Guest WiFi (15 hosts)

Create an IP addressing table using VLSM on a 192.168.1.0/24 base network.

## Task 2: Build in Packet Tracer
- 1 Router (edge), 1 Core Switch, 2 Access Switches, PCs/servers per VLAN
- Configure VLANs, trunking, inter-VLAN routing
- Apply your VLSM addressing plan
- Configure basic device security (passwords, encrypted)

## Task 3: Verify Full Connectivity
```
ping (between same-VLAN devices)
ping (between different-VLAN devices, via router)
show ip route
show vlan brief
```
All pings should succeed before moving to Task 4.

## Task 4: Fault Injection Exercise
Introduce these 3 faults one at a time, and document how you diagnosed and fixed each:

**Fault 1**: Change a PC's subnet mask to an incorrect value
**Fault 2**: Assign a switch port to the wrong VLAN
**Fault 3**: Remove `no shutdown` from a router sub-interface

For each fault: note the symptom observed, the diagnostic commands used, and the fix applied.

## Results
| Item | Value |
|---|---|
| IP addressing table completed (Y/N) | |
| Full topology built (Y/N) | |
| All initial pings successful (Y/N) | |
| Fault 1 diagnosed and fixed (Y/N) | |
| Fault 2 diagnosed and fixed (Y/N) | |
| Fault 3 diagnosed and fixed (Y/N) | |

## Screenshots
```
![IP Addressing Table](Screenshots/ip-table.png)
![Full Topology](Screenshots/capstone-topology.png)
![Fault Diagnosis](Screenshots/fault-diagnosis.png)
```

## Lab Summary
Write a short "incident report" style summary for each of the 3 faults: symptom, root cause, fix. This is genuinely good practice for how real NOC/network troubleshooting documentation looks.
