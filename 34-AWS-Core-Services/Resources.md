# Day 34 - Resources

## Tools Used
- AWS EC2, S3, RDS, Lambda
- AWS CLI

## Commands Reference
| Purpose | Command |
|---|---|
| Launch EC2 (CLI) | `aws ec2 run-instances --image-id <ami> --instance-type t2.micro` |
| List EC2 instances | `aws ec2 describe-instances` |
| Stop/Terminate instance | `aws ec2 stop-instances` / `terminate-instances --instance-ids <id>` |
| Create S3 bucket | `aws s3 mb s3://bucket-name` |
| Upload to S3 | `aws s3 cp file s3://bucket-name/` |
| Delete S3 bucket | `aws s3 rb s3://bucket-name --force` |
| Create RDS instance | `aws rds create-db-instance ...` |

## Key Terms Glossary
- **AMI**: Amazon Machine Image, the OS template for EC2
- **Bucket**: S3's storage container for objects
- **Serverless**: no server management required (Lambda model)
- **Security Group**: virtual firewall controlling traffic to AWS resources

## Further Reading
- AWS official documentation per service (docs.aws.amazon.com)
- AWS Skill Builder free courses (training.aws.amazon.com)

## Skills Gained Today
- EC2 instance launch and SSH access
- S3 bucket creation, upload, and permission awareness
- Lambda function deployment and testing
- Resource cleanup discipline to avoid unexpected billing
