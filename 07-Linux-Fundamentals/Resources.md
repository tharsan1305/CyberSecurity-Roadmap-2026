# Day 07 - Resources

## Tools Used
- Ubuntu (VM or WSL)
- Kali Linux (reference, used heavily later in Pentesting phase)

## Commands Reference
| Purpose | Command |
|---|---|
| Update package lists | `sudo apt update` |
| Upgrade packages | `sudo apt upgrade -y` |
| Install package | `sudo apt install <package> -y` |
| Remove package | `sudo apt remove <package> -y` |
| Check service status | `systemctl status <service>` |
| List running services | `systemctl list-units --type=service --state=running` |
| Check OS info | `cat /etc/os-release` |
| Check kernel info | `uname -a` |

## Key Terms Glossary
- **FHS**: Filesystem Hierarchy Standard
- **Distro**: a packaged Linux OS variant (Ubuntu, Kali, CentOS, etc.)
- **systemd**: modern Linux init/service management system
- **Kernel**: the core of the OS managing hardware/resources

## Further Reading
- The Linux Documentation Project (tldp.org)
- Ubuntu official documentation (help.ubuntu.com)

## Skills Gained Today
- Linux filesystem navigation and FHS understanding
- Package management with apt
- systemd service inspection
- Distro awareness for security tooling context
