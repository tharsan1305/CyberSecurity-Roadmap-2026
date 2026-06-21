# Day 19 - Subnetting

## Goal
Master subnetting calculations - one of the most heavily tested practical skills in networking interviews and CCNA certification.

---

## 1. CIDR Notation

CIDR (Classless Inter-Domain Routing) notation expresses a subnet mask as a suffix: `/24` means the first 24 bits are the network portion.

```
192.168.1.0/24
```
This means: 24 bits for network, 8 bits remaining for hosts (32 - 24 = 8).

## 2. Subnet Masks

A subnet mask separates the network portion of an IP from the host portion.

| CIDR | Subnet Mask | Hosts Available |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /30 | 255.255.255.252 | 2 |

Formula for usable hosts: `2^(host bits) - 2` (subtract network address and broadcast address).

## 3. VLSM (Variable Length Subnet Masking)

VLSM allows subnets of different sizes within the same network, rather than forcing every subnet to be the same size - far more efficient use of IP space.

Example: a /24 network needing departments of different sizes:
```
Sales (50 hosts needed)     -> /26 (62 usable hosts)
Engineering (20 hosts needed) -> /27 (30 usable hosts)
Guest WiFi (10 hosts needed)   -> /28 (14 usable hosts)
Point-to-point link (2 hosts)    -> /30 (2 usable hosts)
```
Without VLSM, you'd be forced to use the same mask everywhere, wasting addresses on smaller subnets.

## 4. Subnet Calculations

### Step-by-step example: Subnet 192.168.1.0/24 into 4 equal subnets

1. Need 4 subnets -> need 2 bits to represent 4 (2^2 = 4)
2. Borrow 2 bits from host portion: /24 becomes /26
3. New subnet mask: 255.255.255.192
4. Block size = 256 - 192 = 64

Resulting subnets:
```
Subnet 1: 192.168.1.0   - 192.168.1.63    (Network: .0, Broadcast: .63, Usable: .1-.62)
Subnet 2: 192.168.1.64  - 192.168.1.127   (Network: .64, Broadcast: .127, Usable: .65-.126)
Subnet 3: 192.168.1.128 - 192.168.1.191   (Network: .128, Broadcast: .191, Usable: .129-.190)
Subnet 4: 192.168.1.192 - 192.168.1.255   (Network: .192, Broadcast: .255, Usable: .193-.254)
```

### Quick trick: the "magic number" method
Magic number = 256 - subnet mask's last non-255 octet. Subnets increment by the magic number.

---

## Interview Questions

**Q1. How many usable hosts are in a /27 subnet?**
2^(32-27) - 2 = 2^5 - 2 = 32 - 2 = 30 usable hosts.

**Q2. What is VLSM and why is it useful?**
Variable Length Subnet Masking - allows different-sized subnets within the same network, avoiding wasted IP addresses compared to using one fixed subnet size everywhere.

**Q3. What is the network address and broadcast address in a subnet, and can they be assigned to hosts?**
The network address is the first address in a subnet (identifies the subnet itself); the broadcast address is the last (used to send to all hosts in the subnet). Neither can be assigned to an individual host.

**Q4. Convert /26 to a subnet mask.**
255.255.255.192

## Key Takeaways
- Learned CIDR notation and subnet mask relationships
- Learned the usable host formula: 2^(host bits) - 2
- Learned VLSM and why it's more efficient than fixed-size subnetting
- Practiced manual subnet calculation with a worked example
