# Day 09 - Resources

## Tools Used
- Ubuntu/Debian Linux (apt-based)
- nginx (test service for service management practice)
- cron / crontab

## Commands Reference
| Purpose | Command |
|---|---|
| Create user with home dir | `sudo useradd -m username` |
| Set password | `sudo passwd username` |
| Add to group | `sudo usermod -aG groupname username` |
| Delete user + home | `sudo userdel -r username` |
| Service status | `systemctl status service` |
| Enable on boot | `systemctl enable service` |
| View service logs | `journalctl -u service` |
| Follow logs live | `journalctl -f` |
| Disk usage summary | `df -h` |
| Directory size | `du -sh path` |
| Edit cron jobs | `crontab -e` |
| List cron jobs | `crontab -l` |

## Key Terms Glossary
- **/etc/passwd**: stores user account information (not passwords)
- **/etc/shadow**: stores hashed passwords, root-only readable
- **Cron**: Linux job scheduler for recurring tasks
- **journalctl**: command to query systemd's logging system (journal)

## Further Reading
- Linux man pages: `man crontab`, `man useradd`, `man systemctl`
- crontab.guru (interactive cron syntax helper)

## Skills Gained Today
- User/group administration
- systemd service management
- Log inspection (journalctl + traditional logs)
- Disk usage monitoring
- Cron job scheduling
