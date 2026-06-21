# Day 48 - Resources

## Tools Used
- Ansible (control node)

## Commands Reference
| Purpose | Command |
|---|---|
| Install Ansible | `pip install ansible --break-system-packages` |
| Test connectivity | `ansible -i inventory.ini <group> -m ping` |
| Run a playbook | `ansible-playbook -i inventory.ini playbook.yml` |
| Run with verbose output | `ansible-playbook -i inventory.ini playbook.yml -v` |
| Check syntax without running | `ansible-playbook playbook.yml --syntax-check` |

## Key Terms Glossary
- **Inventory**: list of managed hosts
- **Playbook**: YAML file defining tasks to execute
- **Module**: pre-built task unit (apt, copy, service, template, etc.)
- **Role**: standardized, reusable playbook organization structure
- **Idempotency**: repeated execution produces the same end state without side effects
- **Jinja2**: templating engine used for dynamic configuration generation

## Further Reading
- Ansible official documentation (docs.ansible.com)
- Ansible Galaxy (galaxy.ansible.com) - community role repository

## Skills Gained Today
- Inventory and Playbook authoring
- Module usage for common automation tasks
- Variables and Jinja2 templating
- Idempotency verification through repeated execution
