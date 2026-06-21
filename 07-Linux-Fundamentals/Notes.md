# Day 07 - Linux Fundamentals

## Goal
Build a conceptual foundation in Linux before diving into commands (Day 08) and administration (Day 09) - Linux is central to most cybersecurity tooling.

---

## 1. Filesystem Hierarchy Standard (FHS)

Linux organizes everything under a single root directory tree (`/`), unlike Windows' drive letters.

Key directories:
| Path | Purpose |
|---|---|
| `/` | Root of the filesystem |
| `/bin` | Essential user binaries (commands) |
| `/etc` | System configuration files |
| `/home` | User home directories |
| `/var` | Variable data (logs, mail, spool) |
| `/var/log` | System and application logs - critical for security analysis |
| `/tmp` | Temporary files |
| `/root` | Home directory for the root user |
| `/usr` | User programs and libraries |
| `/dev` | Device files |
| `/proc` | Virtual filesystem exposing kernel/process info |

## 2. Distributions

A "distro" packages the Linux kernel with software, package managers, and configuration into a usable OS.

Common distros relevant to this roadmap:
- **Ubuntu**: beginner-friendly, widely used for servers and general use
- **Kali Linux**: Debian-based, pre-loaded with penetration testing tools (used heavily in the Pentesting phase)
- **CentOS / Rocky Linux**: enterprise-focused, RHEL-compatible

## 3. Package Managers

Tools for installing, updating, and removing software.

- **apt** (Debian/Ubuntu): `apt install`, `apt update`, `apt remove`
- **yum / dnf** (RHEL/CentOS/Fedora): `dnf install`, `dnf update`

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install nmap -y
```

## 4. Boot Process & Init Systems

Linux boot sequence (simplified):
```
BIOS/UEFI -> Bootloader (GRUB) -> Kernel loads -> Init system starts -> Login prompt
```

**Init systems** manage startup of services:
- **systemd** (modern, used by Ubuntu, CentOS 7+, most current distros)
- **SysVinit** (older, mostly legacy now)

systemd commands:
```bash
systemctl status <service>
systemctl start <service>
systemctl enable <service>    # start on boot
```

---

## Interview Questions

**Q1. What is the FHS and why does it matter?**
The Filesystem Hierarchy Standard defines the standard directory structure in Linux, ensuring consistency across distros so admins/scripts know where to find things (e.g., logs always in `/var/log`).

**Q2. What's the difference between apt and yum/dnf?**
Both are package managers; apt is used on Debian/Ubuntu-based distros, yum/dnf on RHEL/CentOS/Fedora-based distros.

**Q3. What is systemd?**
The modern init system used by most current Linux distros, responsible for managing services, startup, and system state.

**Q4. Why is Kali Linux commonly used in security work?**
It's a Debian-based distro pre-loaded with penetration testing and security tools, saving setup time for security professionals.

## Key Takeaways
- Learned the Linux Filesystem Hierarchy Standard and key directories
- Understood differences between major distros (Ubuntu, Kali, CentOS)
- Learned package managers: apt, yum/dnf
- Understood the Linux boot process and systemd init system
