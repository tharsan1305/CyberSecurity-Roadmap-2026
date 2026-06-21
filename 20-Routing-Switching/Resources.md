# Day 20 - Resources

## Tools Used
- Cisco Packet Tracer

## Commands Reference
| Purpose | Command |
|---|---|
| Create VLAN | `vlan <id>` then `name <name>` |
| Assign access VLAN to port | `switchport access vlan <id>` |
| Configure trunk port | `switchport mode trunk` |
| Configure sub-interface (router-on-a-stick) | `interface gi0/0.<vlan>` then `encapsulation dot1Q <vlan>` |
| Add static route | `ip route <network> <mask> <next-hop>` |
| Enable OSPF | `router ospf 1` then `network <net> <wildcard> area 0` |

## Key Terms Glossary
- **Static Route**: manually configured routing entry
- **OSPF/EIGRP/BGP**: dynamic routing protocols (interior/interior/exterior gateway respectively)
- **VLAN**: Virtual LAN, logical network segmentation
- **Trunk Port**: carries multiple VLANs' traffic between switches (802.1Q tagging)
- **STP**: Spanning Tree Protocol, prevents switching loops
- **Router-on-a-Stick**: single router interface with sub-interfaces handling inter-VLAN routing

## Further Reading
- Cisco Networking Academy: Routing and Switching Essentials course
- Cisco official documentation: OSPF and VLAN configuration guides

## Skills Gained Today
- VLAN creation and trunk port configuration
- Router-on-a-stick inter-VLAN routing
- Static routing configuration
- Conceptual understanding of OSPF, EIGRP, BGP, and STP
