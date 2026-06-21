# Day 35 - Resources

## Tools Used
- AWS VPC Console, EC2, Security Groups, NACLs

## Commands Reference
| Purpose | Command |
|---|---|
| Create VPC (CLI) | `aws ec2 create-vpc --cidr-block 10.0.0.0/16` |
| Create subnet | `aws ec2 create-subnet --vpc-id <id> --cidr-block 10.0.1.0/24` |
| Create security group | `aws ec2 create-security-group --group-name name --vpc-id <id>` |
| Authorize SG ingress | `aws ec2 authorize-security-group-ingress --group-id <id> --protocol tcp --port 22 --cidr <your-ip>/32` |

## Key Terms Glossary
- **VPC**: Virtual Private Cloud, isolated network within AWS
- **Internet Gateway**: allows VPC resources to communicate with the internet
- **NAT Gateway**: allows private subnet outbound-only internet access
- **ALB/NLB**: Application/Network Load Balancer

## Further Reading
- AWS VPC official documentation and FAQs
- AWS Well-Architected Framework: Reliability Pillar (networking sections)

## Skills Gained Today
- VPC and subnet design (public/private)
- Internet Gateway and route table configuration
- Security Group vs NACL practical distinction
- Load balancer type selection awareness
