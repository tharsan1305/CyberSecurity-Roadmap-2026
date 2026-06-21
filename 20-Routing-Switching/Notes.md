# Day 20 - Routing & Switching

## Goal
Understand how routers move traffic between networks and how switches handle traffic within a network - core CCNA territory.

---

## 1. Static Routing

Manually configured routes - the administrator explicitly tells the router how to reach specific networks.

```
ip route <destination-network> <subnet-mask> <next-hop-ip>
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

Pros: predictable, simple for small networks, no protocol overhead.
Cons: doesn't scale, doesn't automatically adapt to network changes/failures.

## 2. Dynamic Routing (OSPF, EIGRP, BGP basics)

Routers automatically learn and share routes with each other.

### OSPF (Open Shortest Path First)
Link-state protocol, calculates the shortest path using a cost metric based on bandwidth. Widely used in enterprise networks, vendor-neutral (open standard).

```
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```

### EIGRP (Enhanced Interior Gateway Routing Protocol)
Cisco-proprietary (though later partially opened), hybrid protocol combining distance-vector and link-state characteristics, fast convergence.

### BGP (Border Gateway Protocol)
The protocol that runs the actual internet - used between Autonomous Systems (ASes, e.g., between ISPs). Path-vector protocol, makes routing decisions based on policies, not just shortest path.

## 3. VLANs

A VLAN (Virtual LAN) logically segments a single physical switch into multiple separate broadcast domains - devices in different VLANs cannot communicate without a router/Layer 3 device, even if physically connected to the same switch.

```
vlan 10
 name Sales
vlan 20
 name Engineering

interface fa0/1
 switchport mode access
 switchport access vlan 10
```

Benefits: improved security (segmentation), reduced broadcast traffic, logical organization independent of physical location.

**Trunk ports**: carry traffic for multiple VLANs between switches, using 802.1Q tagging to identify which VLAN each frame belongs to.

```
interface gi0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

## 4. Switching Concepts (STP, Trunking)

### STP (Spanning Tree Protocol)
Prevents network loops in switched networks with redundant links, which would otherwise cause broadcast storms. STP elects a root bridge and blocks redundant paths, activating them only if the primary path fails.

### Inter-VLAN Routing
Since VLANs can't communicate natively, a Layer 3 device (router or Layer 3 switch) is needed. Common method: "router on a stick" - a single router interface with sub-interfaces, one per VLAN.

```
interface gi0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface gi0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

---

## Interview Questions

**Q1. Difference between static and dynamic routing?**
Static routes are manually configured and fixed; dynamic routing protocols (OSPF, EIGRP, BGP) automatically learn and adapt routes based on network changes.

**Q2. What is a VLAN and why use one?**
A Virtual LAN logically segments a switch into separate broadcast domains, improving security and reducing unnecessary broadcast traffic, independent of physical device location.

**Q3. What does STP prevent?**
Network loops in switched networks with redundant links, which would otherwise cause broadcast storms.

**Q4. What protocol runs the internet's core routing between ISPs?**
BGP (Border Gateway Protocol).

## Key Takeaways
- Learned static vs dynamic routing trade-offs
- Learned OSPF, EIGRP, and BGP at a conceptual level
- Learned VLAN segmentation and trunk port configuration
- Learned STP's role in preventing switching loops
- Learned inter-VLAN routing via router-on-a-stick
