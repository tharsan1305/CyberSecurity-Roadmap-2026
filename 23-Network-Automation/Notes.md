# Day 23 - Network Automation

## Goal
Learn to automate repetitive network engineering tasks using Python and Ansible instead of manual CLI configuration - a core skill bridging networking and DevOps.

---

## 1. Why Network Automation?
Manually configuring hundreds of routers/switches one by one is slow and error-prone. Automation enables consistent, repeatable, auditable configuration changes at scale.

Common use cases:
- Bulk configuration deployment
- Configuration backup across devices
- Compliance auditing (checking configs match a standard)
- Automated troubleshooting/diagnostics

## 2. Python for Networking

### Netmiko
A Python library that simplifies SSH connections to network devices (Cisco, Juniper, Arista, etc.) by handling vendor-specific quirks.

```python
from netmiko import ConnectHandler

device = {
    "device_type": "cisco_ios",
    "host": "192.168.1.1",
    "username": "admin",
    "password": "password",
}

connection = ConnectHandler(**device)
output = connection.send_command("show ip interface brief")
print(output)
connection.disconnect()
```

### Paramiko
A lower-level Python SSH library that Netmiko is built on top of. Useful when you need raw SSH control or when working with non-network devices over SSH.

```python
import paramiko

client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
client.connect("192.168.1.1", username="admin", password="password")
stdin, stdout, stderr = client.exec_command("show version")
print(stdout.read().decode())
client.close()
```

## 3. Ansible for Network Devices

Ansible uses **playbooks** (YAML files) to define desired device state, and pushes configuration via SSH - no agent needed on the network device.

Example playbook structure:
```yaml
---
- name: Configure Cisco Switch
  hosts: switches
  gather_facts: no
  connection: network_cli

  tasks:
    - name: Set hostname
      ios_config:
        lines:
          - hostname SW1-LAB
```

Inventory file example:
```ini
[switches]
192.168.1.1

[switches:vars]
ansible_network_os=ios
ansible_user=admin
ansible_password=password
```

## 4. API-Based Automation
Modern network devices (especially cloud-managed ones like Meraki, or newer Cisco platforms) expose REST APIs for configuration - avoiding CLI parsing entirely.

```python
import requests

response = requests.get(
    "https://api.meraki.com/api/v1/organizations",
    headers={"X-Cisco-Meraki-API-Key": "your-api-key"}
)
print(response.json())
```

## 5. Config Backup/Deployment Scripts
A common automation pattern: loop through a list of devices, pull running-config, save with timestamp.

```python
from netmiko import ConnectHandler
from datetime import datetime

devices = [
    {"device_type": "cisco_ios", "host": "192.168.1.1", "username": "admin", "password": "pass"},
    {"device_type": "cisco_ios", "host": "192.168.1.2", "username": "admin", "password": "pass"},
]

for dev in devices:
    conn = ConnectHandler(**dev)
    config = conn.send_command("show running-config")
    filename = f"{dev['host']}_{datetime.now().strftime('%Y%m%d')}.txt"
    with open(filename, "w") as f:
        f.write(config)
    conn.disconnect()
```

---

## Interview Questions

**Q1. What is Netmiko used for?**
A Python library that simplifies SSH connections to network devices, handling vendor-specific CLI quirks automatically.

**Q2. Difference between Netmiko and Paramiko?**
Paramiko is a low-level generic SSH library; Netmiko is built on top of it specifically for network device CLI automation, with built-in support for many vendors.

**Q3. Why use Ansible for network devices instead of scripts?**
Ansible playbooks are declarative (define desired end state), idempotent, agentless, and easier to maintain/audit at scale than custom scripts.

**Q4. What's a common real-world use case for network automation?**
Automated configuration backups across all devices on a schedule, ensuring a recovery point exists if a device fails or is misconfigured.

## Key Takeaways
- Understood why network automation matters at scale
- Learned Netmiko and Paramiko for Python-based SSH device automation
- Learned Ansible playbook/inventory structure for network devices
- Understood API-based automation as a modern alternative to CLI scraping
- Practiced the config backup automation pattern
