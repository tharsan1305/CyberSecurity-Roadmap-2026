# Day 49 - Resources

## Tools Used
- Terraform CLI
- AWS provider (requires configured AWS CLI credentials)

## Commands Reference
| Purpose | Command |
|---|---|
| Initialize working directory | `terraform init` |
| Preview changes | `terraform plan` |
| Apply changes | `terraform apply` |
| Destroy managed resources | `terraform destroy` |
| Format configuration files | `terraform fmt` |
| Validate configuration syntax | `terraform validate` |

## Key Terms Glossary
- **HCL**: HashiCorp Configuration Language
- **Provider**: plugin enabling Terraform to manage a specific platform
- **Resource**: an infrastructure object managed by Terraform
- **State File**: tracks current managed infrastructure (`terraform.tfstate`)
- **Declarative**: describing desired end state rather than step-by-step instructions

## Further Reading
- Terraform official documentation (developer.hashicorp.com/terraform)
- Terraform Registry (registry.terraform.io) - browse providers and modules

## Skills Gained Today
- Terraform installation and basic workflow (init, plan, apply, destroy)
- AWS resource provisioning via HCL
- Understanding state tracking and drift detection
- Safe infrastructure change review before applying
