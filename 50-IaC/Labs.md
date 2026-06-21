# Day 50 - Lab: Combined Terraform + Ansible Workflow

## Objective
Provision an EC2 instance with Terraform, then configure it with Ansible - demonstrating the full IaC pipeline pattern, and observe drift detection.

## Task 1: Provision with Terraform
```hcl
# main.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_security_group" "lab_sg" {
  name = "lab-sg"
  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["YOUR_IP/32"]
  }
  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

resource "aws_instance" "lab_server" {
  ami                    = "ami-0c55b159cbfafe1f0"
  instance_type          = "t2.micro"
  key_name               = "your-key-pair"
  vpc_security_group_ids = [aws_security_group.lab_sg.id]

  tags = {
    Name = "IaC-Lab-Server"
  }
}

output "instance_ip" {
  value = aws_instance.lab_server.public_ip
}
```
```bash
terraform init
terraform apply
```

## Task 2: Capture Output and Build Ansible Inventory
```bash
terraform output -raw instance_ip
echo "[lab_server]" > inventory.ini
echo "$(terraform output -raw instance_ip) ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/your-key.pem" >> inventory.ini
```

## Task 3: Configure with Ansible
```yaml
# configure.yml
- name: Configure lab server
  hosts: lab_server
  become: yes
  tasks:
    - name: Install nginx
      yum:
        name: nginx
        state: present
    - name: Start nginx
      service:
        name: nginx
        state: started
```
```bash
ansible-playbook -i inventory.ini configure.yml
curl http://$(terraform output -raw instance_ip)
```

## Task 4: Simulate and Detect Drift
Manually change the security group in the AWS Console (e.g., add a rule allowing port 80 from anywhere), then:
```bash
terraform plan
```
Observe Terraform flags the manual change as drift.

## Results
| Item | Value |
|---|---|
| EC2 instance provisioned (Y/N) | |
| Ansible configuration applied successfully (Y/N) | |
| nginx accessible via curl (Y/N) | |
| Drift detected by terraform plan (Y/N) | |

## Cleanup
```bash
terraform destroy
```

## Screenshots
```
![Terraform Apply Output](Screenshots/tf-apply.png)
![Ansible Configuration](Screenshots/ansible-config.png)
![Drift Detected](Screenshots/drift-detected.png)
```

## Lab Summary
Note exactly what `terraform plan` reported when it detected the manual console change - this is a very concrete, real demonstration of why teams enforce "everything through IaC."
