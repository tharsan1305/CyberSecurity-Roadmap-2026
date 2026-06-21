# Day 48 - Lab: Ansible Automation

## Prerequisite
```bash
pip install ansible --break-system-packages
# or
sudo apt install ansible -y
```
Need at least one target host (a VM, or use `localhost` with `ansible_connection=local` for testing without a separate machine).

## Task 1: Create an Inventory File
```ini
[local]
localhost ansible_connection=local
```

## Task 2: Test Connectivity
```bash
ansible -i inventory.ini local -m ping
```

## Task 3: Write and Run a Basic Playbook
```yaml
---
- name: Lab playbook
  hosts: local
  tasks:
    - name: Create a test file
      copy:
        content: "Created by Ansible on Day 48"
        dest: /tmp/ansible_test.txt

    - name: Show file content
      command: cat /tmp/ansible_test.txt
      register: output

    - debug:
        var: output.stdout
```
```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Task 4: Demonstrate Idempotency
Run the same playbook again:
```bash
ansible-playbook -i inventory.ini playbook.yml
```
Observe: the "Create a test file" task shows "ok" (not "changed") on the second run, since the file already exists with the same content.

## Task 5: Use a Jinja2 Template
```bash
cat << 'EOF' > config.conf.j2
app_name={{ app_name }}
app_port={{ app_port }}
EOF
```
```yaml
- name: Deploy templated config
  hosts: local
  vars:
    app_name: "LabApp"
    app_port: 8080
  tasks:
    - name: Generate config from template
      template:
        src: config.conf.j2
        dest: /tmp/app_config.conf
```
```bash
ansible-playbook -i inventory.ini template_playbook.yml
cat /tmp/app_config.conf
```

## Results
| Item | Value |
|---|---|
| Ping test successful (Y/N) | |
| Playbook ran successfully (Y/N) | |
| Idempotency confirmed (2nd run = "ok" not "changed") (Y/N) | |
| Template rendered correctly (Y/N) | |

## Screenshots
```
![Ping Test](Screenshots/ansible-ping.png)
![Playbook Run](Screenshots/playbook-run.png)
![Idempotency Confirmed](Screenshots/idempotency.png)
```

## Lab Summary
Note the exact output difference between the first and second playbook run, confirming idempotency in practice rather than just by definition.
