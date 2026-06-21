# Day 35 - Lab: VPC Design and Configuration

## Task 1: Create a Custom VPC
Console: VPC -> Create VPC -> CIDR 10.0.0.0/16, name "lab-vpc"

## Task 2: Create Public and Private Subnets
```
Public Subnet: 10.0.1.0/24
Private Subnet: 10.0.2.0/24
```

## Task 3: Create and Attach Internet Gateway
1. VPC -> Internet Gateways -> Create -> Attach to lab-vpc
2. Edit public subnet's route table: add route 0.0.0.0/0 -> Internet Gateway

## Task 4: Configure Security Group
Create a Security Group allowing:
- Inbound: TCP 22 from your IP only
- Inbound: TCP 80 from 0.0.0.0/0
- Outbound: all traffic (default)

## Task 5: Launch an EC2 in the Public Subnet
Launch a t2.micro in the public subnet, using the security group created above. Verify you can SSH in using only your allowed IP.

## Task 6: Test NACL Behavior (Optional Deep Dive)
Modify the subnet's NACL to explicitly deny a port (e.g., deny inbound 22), and observe that SSH now fails even though the Security Group allows it - demonstrating that both layers must permit traffic.

## Results
| Item | Value |
|---|---|
| VPC created with correct CIDR (Y/N) | |
| Public/private subnets created (Y/N) | |
| Internet Gateway attached (Y/N) | |
| EC2 reachable via SSH (Y/N) | |
| NACL deny test confirmed both layers matter (Y/N) | |

## Cleanup
Terminate EC2, delete VPC and associated resources to avoid charges.

## Screenshots
```
![VPC Diagram](Screenshots/vpc-diagram.png)
![Security Group Rules](Screenshots/sg-rules.png)
![NACL Test](Screenshots/nacl-test.png)
```

## Lab Summary
Note how the Security Group + NACL interaction worked - this distinction is commonly tested in interviews and easy to misunderstand without hands-on practice.
