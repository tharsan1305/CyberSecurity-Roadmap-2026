# 78 - Digital Forensics (DFIR)

## Overview
Digital Forensics is the science of collecting, preserving, analyzing, and presenting digital evidence in a legally admissible way. DFIR combines Digital Forensics with Incident Response.

---

## 1. Evidence Collection & Chain of Custody

### Chain of Custody
A documented record of who collected, handled, transferred, or examined evidence. Critical for legal proceedings.

### Evidence Collection Principles
- **Order of Volatility**: Collect most volatile data first
  ```
  CPU registers & cache → RAM → Swap space → Network connections
  → Running processes → Disk → Backup media → Printed records
  ```
- Never write to the original evidence — use write blockers
- Hash everything: calculate MD5/SHA256 before and after imaging
- Document every action with timestamps

### Write Blockers
Hardware or software tools that prevent any write operations to evidence media.
- Hardware: Tableau, WiebeTech write blockers
- Software: `mount -o ro` (Linux read-only mount)

---

## 2. Disk Forensics

### Creating a Forensic Image
```bash
# Using dd (Linux)
dd if=/dev/sdb of=/evidence/disk_image.dd bs=512 status=progress

# Using dcfldd (better - shows progress and hashes)
dcfldd if=/dev/sdb of=/evidence/disk_image.dd hash=sha256 hashlog=hash.txt

# Using FTK Imager (Windows GUI tool - free)
# File → Create Disk Image → Select source → E01 format
```

### Analyzing a Disk Image – Autopsy
1. Create new case in Autopsy
2. Add data source (disk image .E01 or .dd)
3. Select ingest modules:
   - File Type Identification
   - Keyword Search
   - Recent Activity
   - Hash Lookup
4. Analyze results:
   - Deleted files (recovered by Autopsy)
   - Browser history, downloads
   - USB device history
   - Recent documents
   - Timeline of file activity

### Important File Locations (Windows)
| Artifact               | Location                                                   |
|------------------------|------------------------------------------------------------|
| User files             | C:\Users\[username]\                                    |
| Browser history (Chrome)| C:\Users\[user]\AppData\Local\Google\Chrome\User Data|
| Recycle Bin            | C:\$Recycle.Bin                                           |
| Prefetch files         | C:\Windows\Prefetch                                      |
| Event logs             | C:\Windows\System32\winevt\Logs                       |
| Registry hives         | C:\Windows\System32\config                             |
| Pagefile               | C:\pagefile.sys                                           |

---

## 3. Memory Forensics – Volatility

### Why Memory Forensics?
- Running processes and their memory contents
- Network connections (established, listening)
- Injected code (fileless malware lives only in RAM)
- Encryption keys and passwords in plaintext
- Evidence that disappears on reboot

### Volatility 3 – Common Commands
```bash
# List running processes
python vol.py -f memory.dmp windows.pslist

# Process tree (shows parent-child relationships)
python vol.py -f memory.dmp windows.pstree

# Network connections
python vol.py -f memory.dmp windows.netstat

# List loaded DLLs for a process
python vol.py -f memory.dmp windows.dlllist --pid 1234

# Dump suspicious process memory
python vol.py -f memory.dmp windows.procdump --pid 1234

# Find injected code (hollow/injected processes)
python vol.py -f memory.dmp windows.malfind

# Scan for malware signatures
python vol.py -f memory.dmp windows.yarascan --yara-rules malware.yar
```

### Capturing RAM
- **Windows**: WinPmem, Belkasoft RAM Capturer (free)
- **Linux**: `/proc/mem`, LiME kernel module
- **VMware**: Suspend VM → .vmem file is the memory image

---

## 4. Timeline Analysis

### Super Timeline with Plaso
```bash
# Create super timeline from disk image
log2timeline.py --parsers win7 timeline.plaso /evidence/disk.E01

# Filter timeline to specific time range
psort.py -o l2tcsv -w output.csv timeline.plaso "date > '2024-01-01 00:00:00' AND date < '2024-01-02 00:00:00'"
```

### Key Timeline Artifacts (Windows)
| Artifact           | What it Shows                          |
|--------------------|----------------------------------------|
| Prefetch           | Program execution times                |
| Event Logs         | Login/logoff, account changes, service install |
| Registry LastWrite | Registry key modification times        |
| NTFS $MFT          | File creation, modification, access    |
| LNK Files          | Recently accessed files/folders        |
| Shellbags          | Folders accessed via Windows Explorer  |
| Browser History    | URLs visited and timestamps            |
