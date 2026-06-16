Why it matters: if RAM is full, the OS starts using disk as overflow ("swap"/"page file"), which is much slower — this is a common cause of a system feeling slow.

Check RAM:
- Windows: `systeminfo`
- Linux: `free -h`

---

### Storage
Permanent, non-volatile memory — data survives after power off.

Types:
- **HDD (Hard Disk Drive)**: mechanical spinning disk, slower, cheaper per GB
- **SSD (Solid State Drive)**: flash-based, no moving parts, much faster than HDD
- **NVMe SSD**: SSD connected via the faster NVMe/PCIe interface instead of older SATA — fastest common consumer storage

Check Storage:
- Windows: `diskmgmt.msc`
- Linux: `lsblk`

---

### Motherboard
The main circuit board that physically and electrically connects every component:
- CPU
- RAM
- Storage
- Network Card
- GPU
- Power supply connections

Think of it as the city road system connecting everything — nothing on the computer works without a path through the motherboard.

---

## 2. Input Devices
Devices that send data **into** the computer:
- Keyboard
- Mouse
- Scanner
- Microphone
- Webcam

---

## 3. Output Devices
Devices that receive data/results **from** the computer:
- Monitor
- Printer
- Speaker
- Projector

---

## 4. Operating System (OS)
Software layer that sits between hardware and the user/applications. Manages hardware so applications don't need to talk to hardware directly.

Examples: Windows 11, Ubuntu Linux, Kali Linux, macOS

Core responsibilities:
- **Memory Management**: allocating RAM to running programs, freeing it when done
- **File Management**: organizing, storing, and retrieving files on storage
- **User Management**: handling accounts, permissions, login sessions
- **Process Management**: scheduling which program gets CPU time and when
- **Security**: enforcing permissions, authentication, and access control

This is the layer where most cybersecurity work eventually connects — OS-level permissions, processes, and logs are central to defense and attack analysis.

---

## 5. File Systems
A file system defines **how data is structured and organized on storage**.

Common types:
- **NTFS** — default on modern Windows; supports permissions, encryption, large file sizes
- **FAT32** — older, simple, widely compatible (USB drives), but has a 4GB single-file size limit
- **exFAT** — modern replacement for FAT32 without the file size limit, used for flash drives/SD cards
- **ext4** — default on most Linux distributions; journaling file system (helps prevent corruption on crash)

---

## 6. Basic Troubleshooting

### Computer Not Turning On
Check, in order:
1. Power cable — properly connected, outlet working
2. Power supply — unit functioning, fan spinning
3. RAM seating — reseat RAM sticks if loose
4. Motherboard LEDs — diagnostic lights indicating which component is failing

### No Internet
Check, in order:
1. Wi-Fi enabled on the device?
2. IP address assigned? (not showing 0.0.0.0 or APIPA 169.254.x.x)
3. Can you ping the gateway (router)?
4. Can you ping an external DNS (e.g., Google DNS 8.8.8.8)?

Commands:

ipconfig          (Windows - view IP config)

ping 8.8.8.8       (test raw internet connectivity, bypassing DNS)

ping google.com    (test DNS resolution + connectivity)


If `ping 8.8.8.8` works but `ping google.com` fails → DNS issue, not a connectivity issue.

### System Slow
Check:
- RAM usage — is it maxed out?
- CPU usage — any single process spiking to 90-100%?
- Disk usage — is storage nearly full, or disk I/O maxed?
- Startup programs — too many apps launching at boot, consuming resources early

Tools:
- Windows: `taskmgr` (Task Manager — Processes, Performance, Startup tabs)
- Linux: `top` (live view of CPU/RAM usage per process) or `htop` if installed

---

## Interview Questions

**Q1. What is RAM?**
Temporary memory used by running applications. Data is lost when power is removed or the process ends.

**Q2. Difference between RAM and Storage?**
| RAM | Storage |
|---|---|
| Temporary (volatile) | Permanent (non-volatile) |
| Faster | Slower |
| Used while programs run | Used to keep files long-term |

**Q3. What is CPU?**
The Central Processing Unit — it executes instructions and performs the calculations that drive every program on the computer.

**Q4. What is an Operating System?**
Software that manages hardware resources (memory, CPU, storage) and provides services so applications can run without directly controlling hardware.

**Q5. What is NTFS?**
A Windows file system used to store and organize files; supports permissions, file encryption, and large file/volume sizes.

**Q6. What's the difference between HDD and SSD?**
HDD uses spinning mechanical disks and is slower; SSD uses flash memory with no moving parts and is significantly faster.

**Q7. Why would a computer be slow even with a fast CPU?**
Bottlenecks elsewhere — insufficient RAM causing swapping, a failing/full disk, too many startup programs, or background processes consuming resources.

---

## Key Takeaways
- Understood core hardware components and their roles: CPU, RAM, Storage, Motherboard
- Learned input/output device categories
- Learned OS responsibilities: memory, file, user, process management, security
- Learned common file systems: NTFS, FAT32, exFAT, ext4
- Practiced a structured troubleshooting approach for boot issues, network issues, and slow performance
- Practiced basic system information commands on both Windows and Linux


---The end ----
