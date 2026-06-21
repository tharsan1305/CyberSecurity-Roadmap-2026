# Day 21 - CCNA

## Goal
Consolidate Topics 17-20 into CCNA exam-aligned practice - this topic ties together networking fundamentals, protocols, subnetting, and routing/switching into the certification context. Given CCNA's breadth, treat this as 2-3 days of focused review and lab practice rather than new conceptual content.

---

## 1. Router & Switch Configuration

Core configuration skills tested in CCNA:
```
enable                      # privileged exec mode
configure terminal            # global config mode
hostname R1                    # set device hostname
interface gi0/0                 # enter interface config
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
copy running-config startup-config    # save config
```

## 2. VLAN & Inter-VLAN Routing
Reviewed in depth in Topic 20 - CCNA expects fluency in VLAN creation, trunk configuration, and router-on-a-stick or Layer 3 switch-based inter-VLAN routing.

## 3. Routing Protocols
CCNA covers OSPF in the most depth (single-area OSPF is a core exam topic). Know the basic configuration, how routers form neighbor adjacencies, and how to verify with:
```
show ip route
show ip ospf neighbor
show ip protocols
```

## 4. WAN Technologies

Concepts CCNA expects familiarity with:
- **Leased Lines**: dedicated point-to-point connections
- **MPLS (Multiprotocol Label Switching)**: efficient packet forwarding using labels instead of full routing lookups at each hop
- **VPN over WAN**: site-to-site connectivity over the public internet (covered Day 26)

## 5. Network Troubleshooting

CCNA troubleshooting methodology generally follows the OSI model - bottom-up or top-down:
```
1. Physical: cables connected? link lights on?
2. Data Link: correct VLAN, trunk working?
3. Network: correct IP, subnet, gateway?
4. Transport: correct ports open, firewall not blocking?
5. Application: is the actual service running?
```

Key verification commands:
```
show ip interface brief    # quick status of all interfaces
show running-config          # current active configuration
show vlan brief               # VLAN assignments
ping / traceroute               # connectivity testing
show interfaces                  # detailed interface stats, errors
```

---

## Interview Questions

**Q1. What command saves your running configuration so it persists after reboot?**
`copy running-config startup-config`

**Q2. What's a structured approach to network troubleshooting?**
Following the OSI model layer by layer (physical connectivity, then data link/VLAN, then IP/routing, then ports/firewalls, then the application itself).

**Q3. What does `show ip interface brief` show you?**
A quick summary of all interfaces, their IP addresses, and their up/down status - a fast first troubleshooting command.

**Q4. What is MPLS used for?**
Efficient WAN packet forwarding using labels rather than full routing table lookups at every hop, commonly used by ISPs for enterprise WAN connectivity.

## Key Takeaways
- Consolidated router/switch configuration fundamentals
- Reinforced VLAN and inter-VLAN routing from Topic 20
- Learned OSPF verification commands
- Learned WAN technology concepts (leased lines, MPLS, VPN)
- Learned a structured, OSI-aligned troubleshooting methodology
