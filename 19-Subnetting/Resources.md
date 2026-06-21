# Day 19 - Resources

## Tools Used
- Cisco Packet Tracer
- Online subnet calculator (subnet-calculator.com, or similar)

## Subnet Mask Quick Reference
| CIDR | Mask | Usable Hosts | Magic Number |
|---|---|---|---|
| /24 | 255.255.255.0 | 254 | 256 |
| /25 | 255.255.255.128 | 126 | 128 |
| /26 | 255.255.255.192 | 62 | 64 |
| /27 | 255.255.255.224 | 30 | 32 |
| /28 | 255.255.255.240 | 14 | 16 |
| /29 | 255.255.255.248 | 6 | 8 |
| /30 | 255.255.255.252 | 2 | 4 |

## Key Formulas
- Usable hosts = 2^(host bits) - 2
- Number of subnets (when borrowing bits) = 2^(borrowed bits)
- Magic number = 256 - (subnet mask's interesting octet)

## Key Terms Glossary
- **CIDR**: Classless Inter-Domain Routing notation
- **VLSM**: Variable Length Subnet Masking
- **Network Address**: first address in a subnet, identifies the subnet itself
- **Broadcast Address**: last address in a subnet, used to address all hosts at once

## Further Reading
- Cisco Networking Academy: Subnetting modules
- "Subnetting Mastery" practice resources (widely available free practice question sets)

## Skills Gained Today
- Manual subnet mask and host count calculation
- VLSM design for mixed-size networks
- Practical IP addressing implementation in Packet Tracer
