# Day 34 - AWS Core Services

## Goal
Learn the 5 most important AWS services - EC2, S3, RDS, Lambda, VPC - that nearly every AWS workload uses.

---

## 1. EC2 (Compute)
Virtual servers in the cloud. Choose an AMI (Amazon Machine Image, the OS template), instance type (size: t2.micro, t3.medium, etc.), storage, and security group (firewall rules).

```bash
aws ec2 run-instances --image-id ami-xxxx --instance-type t2.micro --key-name mykey
aws ec2 describe-instances
aws ec2 stop-instances --instance-ids i-xxxxx
```

## 2. S3 (Storage)
Object storage service - stores files ("objects") in "buckets." Not a filesystem; accessed via API/HTTP.

```bash
aws s3 mb s3://my-unique-bucket-name
aws s3 cp file.txt s3://my-unique-bucket-name/
aws s3 ls s3://my-unique-bucket-name/
```

Security note: misconfigured public S3 buckets are one of the most common real-world cloud breaches - always review bucket permissions.

## 3. RDS (Database)
Managed relational database service (MySQL, PostgreSQL, etc.) - AWS handles patching, backups, and scaling.

```bash
aws rds create-db-instance --db-instance-identifier mydb --db-instance-class db.t2.micro --engine mysql --master-username admin --master-user-password password123 --allocated-storage 20
```

## 4. Lambda (Serverless)
Run code without managing servers - pay only for execution time, triggered by events (API calls, S3 uploads, schedules).

```python
def lambda_handler(event, context):
    return {"statusCode": 200, "body": "Hello from Lambda"}
```

## 5. VPC (Networking)
Your isolated virtual network within AWS - subnets, route tables, internet gateways, security groups (covered deeper Day 35).

---

## Interview Questions

**Q1. What is EC2 and what determines its cost?**
Virtual servers in AWS; cost depends on instance type, running hours, storage, and data transfer.

**Q2. What is S3 used for, and what's a common security mistake with it?**
Object storage for files; a common mistake is misconfiguring bucket permissions, accidentally making it publicly accessible.

**Q3. What's the benefit of Lambda over EC2 for certain workloads?**
No server management needed, automatic scaling, and pay-only-for-execution-time pricing - ideal for event-driven, intermittent workloads.

**Q4. What does RDS manage on your behalf compared to running a database on EC2 yourself?**
Patching, automated backups, and easier scaling/replication - reducing operational overhead.

## Key Takeaways
- Learned EC2 (compute), S3 (storage), RDS (database), Lambda (serverless), and VPC (networking) basics
- Learned basic AWS CLI commands for each service
- Understood S3 bucket misconfiguration as a common real-world security risk
