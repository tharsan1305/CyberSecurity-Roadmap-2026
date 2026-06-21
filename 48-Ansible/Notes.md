# Day 48 - Ansible

## Goal
Learn Ansible for configuration management and automation - already touched in Topic 23 (Network Automation), today goes deeper into general server/infrastructure automation.

---

## 1. Inventory & Playbooks

**Inventory**: defines the hosts Ansible manages.
```ini
[webservers]
192.168.1.10
192.168.1.11

[databases]
192.168.1.20

[webservers:vars]
ansible_user=admin
```

**Playbook**: a YAML file defining a set of tasks to run against inventory hosts.
```yaml
---
- name: Configure web servers
  hosts: webservers
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start nginx service
      service:
        name: nginx
        state: started
        enabled: yes
```

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## 2. Modules & Roles

**Modules**: the building blocks of tasks - pre-built units handling specific actions (apt, copy, service, user, file, etc.). Ansible includes hundreds of modules covering most common automation needs.

**Roles**: a structured way to organize playbooks for reusability, with a standard directory layout:
```
roles/
  webserver/
    tasks/
      main.yml
    handlers/
      main.yml
    templates/
    files/
    vars/
      main.yml
```

```yaml
- name: Apply webserver role
  hosts: webservers
  roles:
    - webserver
```

## 3. Variables & Templates (Jinja2)

Variables make playbooks reusable across different environments.
```yaml
vars:
  app_port: 5000
  app_env: production
```

**Jinja2 templates** generate configuration files dynamically based on variables.
```
# nginx.conf.j2
server {
    listen {{ app_port }};
    server_name {{ inventory_hostname }};
}
```
```yaml
- name: Deploy nginx config
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/sites-available/default
```

## 4. Idempotency Concept

A core Ansible principle: running a playbook multiple times produces the same end state, without unintended side effects or duplicate changes.

Example: the "Install nginx" task above checks if nginx is already installed - if it is, Ansible reports "ok" (no change) rather than reinstalling. This makes playbooks safe to run repeatedly, which is essential for reliable automation.

---

## Interview Questions

**Q1. What is an Ansible Inventory?**
A file defining the hosts (and groupings/variables) that Ansible will manage and run tasks against.

**Q2. What does idempotency mean in the context of Ansible?**
Running the same playbook multiple times produces the same end state without unintended side effects - tasks check current state before making changes.

**Q3. What is the purpose of an Ansible Role?**
Organizing playbooks into a reusable, standardized directory structure (tasks, handlers, templates, variables) for better maintainability across projects.

**Q4. What does Jinja2 templating allow you to do in Ansible?**
Dynamically generate configuration files using variables, enabling the same template to produce different output per host/environment.

## Key Takeaways
- Learned Inventory and Playbook structure
- Learned Modules and Roles for reusable automation
- Learned Variables and Jinja2 templating for dynamic configuration
- Learned idempotency as a core Ansible design principle
