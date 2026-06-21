# Day 10 - Resources

## Tools Used
- OpenSSH (key generation, hardening)
- Nginx / Apache2
- ufw / iptables
- rsync, tar

## Commands Reference
| Purpose | Command |
|---|---|
| Generate SSH key | `ssh-keygen -t ed25519 -C "email"` |
| Copy key to server | `ssh-copy-id user@host` |
| Restart SSH service | `sudo systemctl restart sshd` |
| Allow port (ufw) | `sudo ufw allow <port>/tcp` |
| Enable firewall | `sudo ufw enable` |
| Check firewall status | `sudo ufw status verbose` |
| Create backup archive | `tar -czvf name.tar.gz /path` |
| Extract archive | `tar -xzvf name.tar.gz -C /destination` |
| Sync/backup to remote | `rsync -avz /source/ user@host:/dest/` |

## Key Terms Glossary
- **sshd_config**: SSH daemon configuration file (`/etc/ssh/sshd_config`)
- **ufw**: Uncomplicated Firewall, simplified iptables frontend
- **Key-based authentication**: SSH login using a cryptographic key pair instead of a password

## Further Reading
- DigitalOcean SSH hardening tutorials (widely referenced, free)
- Nginx official documentation
- ufw official documentation (Ubuntu wiki)

## Skills Gained Today
- SSH key generation and hardening
- Web server installation and basic configuration
- Firewall rule management with ufw
- Server monitoring command fluency
- Backup and restore procedures
