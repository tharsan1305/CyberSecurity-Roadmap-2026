# Day 49 - Terraform

## Goal
Learn Infrastructure as Code (IaC) provisioning with Terraform - while Ansible (Topic 48) configures existing systems, Terraform provisions the infrastructure itself (servers, networks, cloud resources).

---

## 1. HCL Syntax

Terraform uses HCL (HashiCorp Configuration Language) - declarative, human-readable.

```hcl
resource "aws_instance" "web_server" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "WebServer"
  }
}
```

Declarative means: you describe the desired end state, and Terraform figures out how to get there - unlike imperative scripting where you specify exact steps.

## 2. Providers & Resources

**Provider**: a plugin that lets Terraform interact with a specific platform (AWS, Azure, GCP, etc.)
```hcl
provider "aws" {
  region = "us-east-1"
}
```

**Resource**: an infrastructure object Terraform manages (an EC2 instance, S3 bucket, VPC, etc.)
```hcl
resource "aws_s3_bucket" "my_bucket" {
  bucket = "my-terraform-lab-bucket-2026"
}
```

## 3. State Management

Terraform tracks the current state of managed infrastructure in a **state file** (`terraform.tfstate`) - this is how it knows what exists and what needs to change on the next apply.

```bash
terraform init        # initialize, download providers
terraform plan          # preview changes
terraform apply           # apply changes
terraform destroy           # tear down all managed resources
```

Important: state files can contain sensitive data and should never be committed to public Git repos - in team environments, state is typically stored remotely (e.g., S3 backend with state locking via DynamoDB) rather than locally.

## 4. Modules

Modules package reusable Terraform configurations, similar conceptually to Ansible Roles.

```hcl
module "web_server" {
  source        = "./modules/ec2-instance"
  instance_type = "t2.micro"
  ami_id        = "ami-0c55b159cbfafe1f0"
}
```

---

## Interview Questions

**Q1. Difference between Terraform and Ansible?**
Terraform provisions infrastructure (creating servers, networks, cloud resources) using a declarative approach with state tracking; Ansible configures existing systems (installing software, managing config files) and is more procedural/task-based, without persistent state tracking in the same way.

**Q2. What is the Terraform state file used for?**
Tracking the current state of managed infrastructure, so Terraform knows what already exists and what changes are needed on subsequent applies.

**Q3. What does `terraform plan` do, and why is it useful?**
Previews what changes would be made without actually applying them - allows reviewing infrastructure changes before committing to them, reducing risk of unintended changes.

**Q4. Why shouldn't a Terraform state file be committed to a public Git repository?**
It can contain sensitive data (resource attributes, sometimes secrets) and reveals infrastructure details that could aid an attacker; it should be stored securely, often in a remote backend.

## Key Takeaways
- Learned HCL syntax and Terraform's declarative approach
- Learned Providers and Resources
- Learned state management and why it matters for security and team workflows
- Learned Modules for reusable infrastructure configuration
