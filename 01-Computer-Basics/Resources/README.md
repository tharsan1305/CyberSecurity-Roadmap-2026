# Day 01 - Resources

## Commands Reference

| Purpose | Windows | Linux |
|---|---|---|
| CPU Info | `wmic cpu get name` | `lscpu` |
| RAM Info | `systeminfo` | `free -h` |
| Disk Info | `diskmgmt.msc` | `lsblk` |
| OS Info | `systeminfo` | `hostnamectl` |
| Network Config | `ipconfig` | `ifconfig` |
| Ping Test | `ping 8.8.8.8` | `ping 8.8.8.8` |
| DNS Test | `ping google.com` | `ping google.com` |
| Task/Process Manager | `taskmgr` | `top` / `htop` |

## Concepts Covered
- Hardware: CPU, RAM, Storage, Motherboard
- Input devices: Keyboard, Mouse, Scanner, Microphone, Webcam
- Output devices: Monitor, Printer, Speaker, Projector
- Operating System responsibilities: Memory, File, User, Process Management, Security
- File Systems: NTFS, FAT32, exFAT, ext4
- Basic troubleshooting: boot issues, no internet, slow system

## Key Terms Glossary
- **Core**: independent processing unit inside a CPU
- **Clock Speed**: CPU cycles per second (GHz)
- **Cache**: small fast memory inside CPU (L1/L2/L3)
- **Volatile memory**: memory that loses data without power (RAM)
- **Non-volatile memory**: memory that retains data without power (Storage)
- **Journaling file system**: file system that logs changes to prevent corruption on crash (ext4)
- **APIPA**: automatic IP (169.254.x.x) assigned when DHCP fails

## Further Reading
- General "how a computer works" / computer hardware basics guides
- Manufacturer specs for your own CPU model (Intel ARK / AMD product pages)
- Microsoft Docs: Windows file systems overview
- Linux man pages: `man lscpu`, `man free`, `man lsblk`, `man hostnamectl`

## Tools Used Today
- Windows: Command Prompt, Task Manager, Disk Management
- Linux: Terminal (bash)
