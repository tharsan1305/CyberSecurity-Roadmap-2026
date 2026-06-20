# Day 23 - Resources

## Tools Used
- Python 3 with Netmiko, Paramiko libraries
- Ansible (with network collections, e.g., `cisco.ios`)
- Cisco Packet Tracer / GNS3 / EVE-NG (for lab simulation without physical hardware)

## Commands Reference
| Purpose | Command/Code |
|---|---|
| Install Netmiko | `pip install netmiko --break-system-packages` |
| Install Ansible | `pip install ansible --break-system-packages` |
| Connect via Netmiko | `ConnectHandler(**device)` |
| Send single command | `conn.send_command("show ...")` |
| Push config | `conn.send_config_set([...])` |
| Run Ansible playbook | `ansible-playbook -i inventory.ini playbook.yml` |

## Key Terms Glossary
- **Idempotency**: running the same automation multiple times produces the same result without unintended side effects
- **Playbook**: Ansible's YAML file defining tasks/desired state
- **Inventory**: Ansible's list of managed hosts/devices
- **SSH (Secure Shell)**: encrypted protocol most network automation tools use to connect to devices

## Further Reading
- Netmiko official GitHub documentation
- Ansible Network Automation documentation (docs.ansible.com)
- Kirk Byers' Python for Network Engineers course material (widely referenced free content)

## Skills Gained Today
- Python-based SSH automation for network devices (Netmiko/Paramiko)
- Ansible playbook structure for network configuration
- Config backup automation pattern
- API-based automation awareness (Meraki/REST API example)
