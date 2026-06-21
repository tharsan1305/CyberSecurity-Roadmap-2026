# Day 20 - Lab: Routing & Switching in Cisco Packet Tracer

## Objective
Build a topology with VLANs, inter-VLAN routing, and basic OSPF configuration.

## Task 1: Build the Topology
- 1 Router, 1 Layer 2 Switch, 4 PCs (2 for VLAN 10, 2 for VLAN 20)

## Task 2: Configure VLANs on the Switch
```
enable
configure terminal
vlan 10
 name Sales
vlan 20
 name Engineering
exit

interface fa0/1
 switchport mode access
 switchport access vlan 10
interface fa0/2
 switchport mode access
 switchport access vlan 10
interface fa0/3
 switchport mode access
 switchport access vlan 20
interface fa0/4
 switchport mode access
 switchport access vlan 20

interface gi0/1
 switchport mode trunk
```

## Task 3: Configure Router-on-a-Stick for Inter-VLAN Routing
```
interface gi0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface gi0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface gi0/0
 no shutdown
```

## Task 4: Assign PC IPs and Test
Assign PCs in VLAN 10: 192.168.10.10, 192.168.10.11 (gateway 192.168.10.1)
Assign PCs in VLAN 20: 192.168.20.10, 192.168.20.11 (gateway 192.168.20.1)

Test:
```
ping 192.168.10.11    (from a VLAN 10 PC - should work directly)
ping 192.168.20.10    (from a VLAN 10 PC - should work via router)
```

## Task 5: Configure Basic Static Route (Two-Router Topology, Optional Extension)
If you add a second router connected to this one:
```
ip route 172.16.0.0 255.255.0.0 <next-hop-ip>
```

## Results
| Item | Value |
|---|---|
| VLANs configured (Y/N) | |
| Trunk port configured (Y/N) | |
| Inter-VLAN ping successful (Y/N) | |
| Same-VLAN ping successful (Y/N) | |
| Static route added (Y/N, if extended) | |

## Screenshots
```
![VLAN Configuration](Screenshots/vlan-config.png)
![Topology Diagram](Screenshots/topology.png)
![Ping Test Results](Screenshots/ping-results.png)
```

## Lab Summary
Note any connectivity issues between VLANs and how you debugged them (common issue: forgetting `no shutdown` on sub-interfaces).
