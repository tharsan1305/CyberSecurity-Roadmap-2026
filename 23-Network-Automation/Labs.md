# Day 23 - Lab: Network Automation

## Objective
Practice Python-based network automation using Netmiko (or simulate with Cisco Packet Tracer/GNS3/EVE-NG if no real device is available).

## Prerequisites
```bash
pip install netmiko --break-system-packages
pip install paramiko --break-system-packages
pip install ansible --break-system-packages
```

If you don't have a physical/virtual router, use a free network simulator (Cisco Packet Tracer, GNS3, or EVE-NG) with SSH enabled on a virtual router.

## Task 1: Connect via Netmiko
```python
from netmiko import ConnectHandler

device = {
    "device_type": "cisco_ios",
    "host": "<device-ip>",
    "username": "<username>",
    "password": "<password>",
}

conn = ConnectHandler(**device)
print(conn.send_command("show ip interface brief"))
conn.disconnect()
```
Record: output received, any connection errors and how you resolved them.

## Task 2: Push a Configuration Change
```python
config_commands = ["interface loopback 1", "ip address 10.10.10.1 255.255.255.255"]
conn = ConnectHandler(**device)
output = conn.send_config_set(config_commands)
print(output)
conn.disconnect()
```

## Task 3: Write a Config Backup Script
Write a Python script that connects to at least one device, pulls `show running-config`, and saves it to a timestamped file.

## Task 4: Ansible Playbook (if lab environment supports it)
Create an inventory file and a simple playbook to set a hostname on a test device. Run with:
```bash
ansible-playbook -i inventory.ini set_hostname.yml
```

## Results
| Item | Value |
|---|---|
| Netmiko connection successful (Y/N) | |
| Command output retrieved | |
| Config change applied (Y/N) | |
| Backup file created (Y/N) | |
| Ansible playbook ran successfully (Y/N) | |

## Screenshots
Save in `Screenshots/`:
```
![Netmiko Output](Screenshots/netmiko-output.png)
![Backup File](Screenshots/backup-file.png)
```

## Lab Summary
Note any errors encountered (auth failures, timeout, vendor mismatches) and how automation compares to manual CLI configuration in terms of speed and risk of error.
