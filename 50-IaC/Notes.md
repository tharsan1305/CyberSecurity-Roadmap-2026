# Day 50 - IaC (Infrastructure as Code)

## Goal
Consolidate the IaC concepts from Terraform (Topic 49) and Ansible (Topic 48) into a broader understanding of Infrastructure as Code as a discipline, and how the two tools work together.

---

## 1. Declarative vs Imperative Approach

**Declarative** (Terraform's approach): describe the desired end state; the tool determines the steps to get there.
```hcl
resource "aws_instance" "web" {
  instance_type = "t2.micro"
}
```

**Imperative** (traditional scripting approach): specify the exact sequence of steps to execute.
```bash
aws ec2 run-instances --instance-type t2.micro ...
# then manually handle "if it already exists, don't recreate it" logic yourself
```

Ansible is mostly declarative for its desired state (e.g., "ensure nginx is installed") but executes as an ordered sequence of tasks - it sits somewhere between the two models.

## 2. Version-Controlled Infrastructure

The core IaC principle: infrastructure configuration lives in version control (Git), just like application code.

Benefits this brings (tying back to Topics 11-12):
- **History**: every infrastructure change is tracked, who/when/why
- **Review**: infrastructure changes can go through Pull Request review before being applied
- **Rollback**: revert to a previous known-good configuration if something breaks
- **Collaboration**: team members work from the same source of truth, not manual console changes that aren't documented anywhere

## 3. Terraform + Ansible Integration

A common real-world pattern: **Terraform provisions, Ansible configures.**

```
Terraform: creates the EC2 instance, VPC, security groups (the "what exists")
   ↓
Ansible: installs software, configures services on that instance (the "how it's set up")
```

Example workflow:
```bash
terraform apply                              # provision infrastructure
terraform output -raw instance_ip > ip.txt    # capture the new instance's IP
ansible-playbook -i ip.txt, configure.yml      # configure it with Ansible
```

Some teams use Terraform's `local-exec` or `remote-exec` provisioners to trigger Ansible directly, though many prefer keeping the two stages separate (provision, then configure) for clarity.

## 4. Drift Detection

**Configuration drift**: when the actual state of infrastructure diverges from what's defined in code - e.g., someone manually changes a security group rule directly in the AWS Console instead of through Terraform.

```bash
terraform plan
```
Running `plan` against existing infrastructure reveals drift - Terraform shows the difference between actual current state and the defined configuration, even if you haven't changed your `.tf` files.

Preventing drift: enforce that ALL infrastructure changes go through IaC (no manual console changes), which ties back to the access control/least privilege discipline from the IAM topics (36-37) - restricting who has direct console write access helps enforce this.

---

## Interview Questions

**Q1. What is configuration drift, and how do you detect it with Terraform?**
When actual infrastructure state diverges from what's defined in code (e.g., a manual console change); `terraform plan` detects and reports this difference.

**Q2. What's the typical division of labor between Terraform and Ansible?**
Terraform provisions infrastructure (creates the resources); Ansible configures those resources (installs/configures software on them) - "provision then configure."

**Q3. Why is version-controlling infrastructure configuration valuable?**
It provides change history, enables peer review via Pull Requests, allows rollback to known-good states, and creates a single source of truth for the whole team.

**Q4. How can an organization prevent configuration drift in practice?**
By enforcing that all infrastructure changes go through IaC pipelines rather than manual console edits, often combined with restricting direct console write access via IAM least privilege.

## Key Takeaways
- Learned declarative vs imperative infrastructure management approaches
- Reinforced version control benefits applied to infrastructure (not just application code)
- Learned the common Terraform + Ansible integration pattern
- Learned configuration drift and how to detect/prevent it
