# Day 49 - Lab: Terraform AWS Provisioning

## Prerequisite
```bash
# Install Terraform (Linux)
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform -y
terraform -version
```
Ensure AWS CLI is configured with credentials (`aws configure`) from earlier AWS topics.

## Task 1: Write a Basic Configuration
```hcl
# main.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "lab_bucket" {
  bucket = "terraform-lab-bucket-<yourname>-2026"
}
```

## Task 2: Initialize and Plan
```bash
terraform init
terraform plan
```
Review the planned changes before applying.

## Task 3: Apply
```bash
terraform apply
```
Type `yes` to confirm. Verify the bucket was created:
```bash
aws s3 ls | grep terraform-lab
```

## Task 4: Modify and Re-Plan
Add a tag to the bucket resource and run `terraform plan` again - observe Terraform detects the drift and shows only the specific change needed.
```hcl
resource "aws_s3_bucket" "lab_bucket" {
  bucket = "terraform-lab-bucket-<yourname>-2026"
  tags = {
    Environment = "Lab"
  }
}
```

## Task 5: Destroy Resources (Cleanup)
```bash
terraform destroy
```
Type `yes` to confirm. Verify the bucket is gone.

## Results
| Item | Value |
|---|---|
| Terraform installed (Y/N) | |
| Plan reviewed before apply (Y/N) | |
| Bucket created successfully (Y/N) | |
| Tag change detected on re-plan (Y/N) | |
| Resources destroyed successfully (Y/N) | |

## Screenshots
```
![Terraform Plan Output](Screenshots/terraform-plan.png)
![Terraform Apply Output](Screenshots/terraform-apply.png)
![Bucket Created](Screenshots/bucket-created.png)
```

## Lab Summary
Note how `terraform plan` clearly showed what would change before you committed to it - reflect on how this compares to making manual changes directly in the AWS Console.
