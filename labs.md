# Day 01 - Lab: System Information Gathering

## Objective
Find and document your own system's CPU, RAM, Disk, and OS details using command-line tools.

## Task 1: Find System Info

### Windows Commands
systeminfo

wmic cpu get name

diskmgmt.msc

### Linux Commands
hostnamectl

lscpu

free -h

lsblk

## Task 2: Troubleshooting Practice

### Check Network Connectivity
ipconfig        (Windows)

ifconfig        (Linux)

ping 8.8.8.8

### Check Running Processes / Resource Usage
taskmgr          (Windows - GUI)

top               (Linux)

## Results (fill in with your own system's output)
- CPU Name:
- RAM Size:
- Disk Size:
- OS Version:
- Ping result to 8.8.8.8 (success/fail, latency):

## Screenshots
Create a `Screenshots/` subfolder inside `01-Computer-Basics/` and save evidence of each command's output there. Reference them here:
