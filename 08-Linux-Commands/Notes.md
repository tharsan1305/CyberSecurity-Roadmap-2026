# Day 08 - Linux Commands

## Goal
Build hands-on command-line fluency - the single most important practical skill for the rest of this roadmap (Linux Administration, Server Admin, Pentesting, SOC work all build on this).

---

## 1. File Operations
```bash
ls -la              list all files with details
cp src dst           copy file
mv src dst           move/rename file
rm file              remove file
rm -rf folder        remove folder recursively (use carefully)
find / -name "*.log" search for files by name
```

## 2. Permissions
```bash
chmod 755 file       change permissions (rwxr-xr-x)
chown user:group file  change ownership
```

Permission notation:
```
rwx rwx rwx
owner group others

r=4, w=2, x=1
755 = rwxr-xr-x (owner: all, group: read+execute, others: read+execute)
```

## 3. Process Management
```bash
ps aux               list all running processes
top                   live process/resource monitor
kill <pid>            terminate process by PID
kill -9 <pid>          force kill
```

## 4. Text Processing
```bash
grep "error" logfile.txt          search for pattern in file
grep -r "TODO" /path/             recursive search
awk '{print $1}' file              print first column
sed 's/old/new/g' file              find and replace
```

## 5. Networking
```bash
ifconfig             (legacy) show network interfaces
ip addr               (modern) show network interfaces
ping <host>            test connectivity
curl <url>              fetch a URL
wget <url>               download a file
```

---

## Interview Questions

**Q1. What does `chmod 755` do?**
Sets permissions to read/write/execute for owner, and read/execute for group and others.

**Q2. Difference between `kill` and `kill -9`?**
`kill` sends a termination signal the process can handle/ignore; `kill -9` (SIGKILL) forcefully terminates immediately, bypassing graceful shutdown.

**Q3. What does `grep -r` do?**
Recursively searches for a pattern across all files within a directory and its subdirectories.

**Q4. Difference between `ifconfig` and `ip addr`?**
`ifconfig` is the legacy command for viewing/configuring network interfaces; `ip addr` is the modern replacement, part of the `iproute2` suite.

## Key Takeaways
- Learned essential file operation commands
- Understood Linux permission notation and chmod/chown
- Learned process management: ps, top, kill
- Learned text processing tools: grep, awk, sed
- Learned basic networking commands
