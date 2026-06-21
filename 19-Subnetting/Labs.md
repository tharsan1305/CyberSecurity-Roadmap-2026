# Day 19 - Lab: Subnetting Practice

## Objective
Practice manual subnet calculations and verify with a subnet calculator, then apply VLSM design in Cisco Packet Tracer.

## Task 1: Manual Calculation Practice
Solve these by hand first, then verify with an online subnet calculator (e.g., subnet-calculator.com):

1. How many usable hosts in 10.0.0.0/22?
2. What is the subnet mask for /29?
3. Split 192.168.10.0/24 into 8 equal subnets - what is the new CIDR and block size?
4. What are the network address, broadcast address, and usable range for 172.16.5.64/26?

## Task 2: VLSM Design Exercise
Given network 10.10.0.0/24, design VLSM subnets for:
- Sales department: 60 hosts
- IT department: 25 hosts
- Guest WiFi: 10 hosts
- Router-to-router link: 2 hosts

Write out the CIDR, subnet mask, and usable range for each.

## Task 3: Implement in Cisco Packet Tracer
1. Build a topology with 1 router, 1 switch, and several PCs representing each department above
2. Assign IP addresses based on your VLSM design from Task 2
3. Verify connectivity within each subnet using `ping`

## Results
| Item | Value |
|---|---|
| Task 1 answers correct | /4 |
| Sales subnet (CIDR/range) | |
| IT subnet (CIDR/range) | |
| Guest WiFi subnet (CIDR/range) | |
| Point-to-point subnet (CIDR/range) | |
| Packet Tracer ping successful (Y/N) | |

## Screenshots
```
![Subnet Calculations](Screenshots/subnet-calc.png)
![Packet Tracer Topology](Screenshots/packet-tracer-topology.png)
![Ping Test](Screenshots/ping-test.png)
```

## Lab Summary
Note which subnetting calculation took longest to work out manually, and whether the "magic number" trick helped speed things up.
