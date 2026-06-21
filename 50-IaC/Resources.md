# Day 50 - Resources

## Tools Used
- Terraform (provisioning)
- Ansible (configuration)
- AWS (target platform)

## Commands Reference
| Purpose | Command |
|---|---|
| Capture Terraform output | `terraform output -raw <output_name>` |
| Run Ansible against Terraform-provisioned host | `ansible-playbook -i inventory.ini configure.yml` |
| Detect drift | `terraform plan` (run against unchanged .tf files) |

## Key Terms Glossary
- **Configuration Drift**: divergence between actual and code-defined infrastructure state
- **Provisioning**: creating infrastructure resources (Terraform's role)
- **Configuration Management**: setting up software/services on existing infrastructure (Ansible's role)
- **Single Source of Truth**: the principle that version-controlled code, not manual changes, defines the real infrastructure state

## Further Reading
- HashiCorp: "Terraform and Ansible: Better Together" (official blog/whitepaper content)
- Martin Fowler's writing on Infrastructure as Code principles (martinfowler.com)

## Skills Gained Today
- End-to-end IaC pipeline: Terraform provision -> Ansible configure
- Practical drift detection and its real-world implications
- Reinforced the "everything through code" IaC discipline
