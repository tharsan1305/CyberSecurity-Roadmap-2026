# Day 22 - Cisco Packet Tracer Labs

## Goal
Consolidate everything learned in Topics 17-21 into a capstone Packet Tracer project - this closes out the Networking foundation phase before moving into Network Automation, Security, and beyond.

---

## 1. Network Topology Design

Good topology design principles:
- Separate logical zones (departments, server farm, guest network) using VLANs
- Plan IP addressing with VLSM before configuring anything
- Build in redundancy where appropriate (though full redundancy/STP tuning is a more advanced topic)
- Document your design before building it (an IP addressing table is standard practice)

## 2. Device Configuration Labs

By this point, you've practiced: hostnames, passwords, VLANs, trunking, inter-VLAN routing, static routes, OSPF. Today's focus is combining all of these into a single coherent, realistic small-business network design.

## 3. Routing/Switching Simulations

A typical small business topology to simulate:
```
Internet (simulated cloud)
   |
[Edge Router] -- WAN link
   |
[Core Switch] -- with VLANs: Sales, IT, Servers, Guest
   |
[Access Switches] -- connecting to end-user PCs
```

## 4. Troubleshooting Scenarios

Practice deliberately breaking things and fixing them - this is genuinely one of the best ways to learn networking deeply:
- Misconfigure a VLAN assignment, then find and fix it
- Disable `no shutdown` on an interface, then diagnose why it's down
- Set a wrong subnet mask, then identify why hosts can't communicate
- Remove a static route, then trace why traffic isn't reaching a destination

---

## Interview Questions

**Q1. What should you do before configuring a network, not just during?**
Design first - plan VLANs, IP addressing (using VLSM where appropriate), and document the design, rather than configuring ad hoc.

**Q2. Name 3 common causes of "device can't reach the internet" in a lab.**
Missing default gateway, interface not enabled (`no shutdown` missing), incorrect VLAN assignment, or a missing/incorrect static/dynamic route.

**Q3. Why is deliberately breaking a lab topology a useful learning exercise?**
It builds real troubleshooting instincts and pattern recognition that reading alone doesn't provide - most real network issues are diagnosed through this same systematic process.

## Key Takeaways
- Practiced designing a realistic small-business network topology
- Combined VLANs, routing, and device configuration into one project
- Practiced structured troubleshooting through deliberately broken scenarios
- Completed the Networking foundation phase (Topics 17-22) of the roadmap
