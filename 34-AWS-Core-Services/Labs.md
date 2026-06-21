# Day 34 - Lab: AWS Core Services Hands-On

## Task 1: Launch an EC2 Instance (Free Tier t2.micro)
Console: EC2 -> Launch Instance -> Amazon Linux 2 AMI -> t2.micro -> create/select key pair -> launch
```bash
aws ec2 describe-instances --query 'Reservations[].Instances[].[InstanceId,State.Name]'
```
SSH in: `ssh -i mykey.pem ec2-user@<public-ip>`

## Task 2: Create and Use an S3 Bucket
```bash
aws s3 mb s3://my-lab-bucket-<yourname>-2026
echo "test file" > test.txt
aws s3 cp test.txt s3://my-lab-bucket-<yourname>-2026/
aws s3 ls s3://my-lab-bucket-<yourname>-2026/
```
Check bucket permissions in console - confirm it is NOT public.

## Task 3: Deploy a Simple Lambda Function
Console: Lambda -> Create Function -> Author from scratch -> Python 3.x
```python
def lambda_handler(event, context):
    return {"statusCode": 200, "body": "Hello from Lambda, Day 34"}
```
Test it via the console Test button.

## Task 4: (Optional, watch Free Tier limits) Create an RDS Instance
Console: RDS -> Create Database -> MySQL -> Free tier template -> db.t2.micro

## Task 5: CLEANUP (Important)
```bash
aws ec2 terminate-instances --instance-ids <id>
aws s3 rb s3://my-lab-bucket-<yourname>-2026 --force
```
Delete RDS instance from console if created, to avoid charges.

## Results
| Item | Value |
|---|---|
| EC2 instance launched (Y/N) | |
| SSH access successful (Y/N) | |
| S3 bucket created and file uploaded (Y/N) | |
| Lambda function tested successfully (Y/N) | |
| All resources cleaned up (Y/N) | |

## Screenshots
```
![EC2 Instance Running](Screenshots/ec2-running.png)
![S3 Bucket Contents](Screenshots/s3-bucket.png)
![Lambda Test Output](Screenshots/lambda-test.png)
```

## Lab Summary
Confirm you terminated/deleted all resources to avoid charges - note the cost shown in Billing Dashboard after cleanup (should remain $0 within Free Tier).
