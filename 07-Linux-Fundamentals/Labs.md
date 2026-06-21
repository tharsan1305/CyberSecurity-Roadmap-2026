# Day 07 - Lab: Linux Fundamentals

## Objective
Explore the Linux filesystem, practice package management, and inspect the init system.

## Prerequisite
Ubuntu VM (VirtualBox/VMware) or WSL (Windows Subsystem for Linux) if no VM available.

## Task 1: Explore the Filesystem
```bash
ls /
ls /var/log
ls /etc | head -20
cat /etc/os-release
```
Record: your distro name/version, and 3 files you see in `/var/log`.

## Task 2: Package Management Practice
```bash
sudo apt update
sudo apt install neofetch -y
neofetch
sudo apt remove neofetch -y
```
Record: any errors during install/remove.

## Task 3: Boot Process & systemd
```bash
systemctl list-units --type=service --state=running
systemctl status ssh
```
Record: count of running services, status of SSH service.

## Task 4: Check Kernel and System Info
```bash
uname -a
hostnamectl
```

## Results
| Item | Value |
|---|---|
| Distro name/version | |
| Files seen in /var/log | |
| Package install successful (Y/N) | |
| Running services count | |
| Kernel version | |

## Screenshots
```
![Filesystem Exploration](Screenshots/filesystem.png)
![Package Install](Screenshots/package-install.png)
![Systemctl Status](Screenshots/systemctl-status.png)
```

## Lab Summary
Note anything that felt unfamiliar coming from Windows, and what `/var/log` contained that stood out.
