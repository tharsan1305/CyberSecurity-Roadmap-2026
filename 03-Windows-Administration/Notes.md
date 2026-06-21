# Day 03 - Windows Administration

## Goal
Learn how to manage users, permissions, services, and system events on Windows - core skills for any Windows-based IT/security role, and foundational before Active Directory.

---

## 1. User & Group Management

Windows manages access through **local users** and **local groups** (on a single machine) or **domain users/groups** (in Active Directory, covered Day 05).

Key concepts:
- **Local User Account**: an account that exists only on one machine
- **Local Group**: a collection of users granted the same permissions (e.g., Administrators, Users, Guests)
- Built-in groups: Administrators (full control), Users (standard, limited), Guests (very limited, often disabled)

Tools:
- `lusrmgr.msc` - Local Users and Groups GUI
- Computer Management (`compmgmt.msc`) - broader admin console including users, groups, disk management, services

Commands (CMD):
```
net user                     (list all local users)
net user <username>          (view details of a user)
net localgroup                (list all local groups)
net localgroup administrators (view members of Administrators group)
```

---

## 2. Permissions (NTFS, Sharing)

Windows has two permission layers that stack:

**NTFS Permissions** - apply to files/folders regardless of how they're accessed (locally or over network)
- Read, Write, Modify, Full Control, List Folder Contents

**Share Permissions** - apply only when accessing a folder over the network
- Read, Change, Full Control

**Important rule**: when both NTFS and Share permissions apply (network access), the **most restrictive** permission wins.

How to check/set:
- Right-click file/folder -> Properties -> Security tab (NTFS permissions)
- Right-click folder -> Properties -> Sharing tab (Share permissions)

---

## 3. Services & Task Scheduler

### Services
Background processes that run independently of user login (e.g., Print Spooler, Windows Update).

Tool: `services.msc`

Key actions:
- Start / Stop / Restart a service
- Set startup type: Automatic, Manual, Disabled
- View service dependencies

Command line:
```
sc query <servicename>
sc start <servicename>
sc stop <servicename>
```

### Task Scheduler
Runs programs/scripts automatically based on triggers (time, login, event).

Tool: `taskschd.msc`

Useful for: automating backups, running scripts at startup, scheduled scans.

---

## 4. Registry Editor

The **Registry** is a hierarchical database storing low-level OS and application settings.

Tool: `regedit`

Main root keys:
- `HKEY_LOCAL_MACHINE (HKLM)` - system-wide settings
- `HKEY_CURRENT_USER (HKCU)` - settings for the currently logged-in user
- `HKEY_CLASSES_ROOT` - file association data
- `HKEY_USERS` - settings for all loaded user profiles

Security relevance: malware often modifies registry run keys (e.g., `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`) to achieve persistence - this is a common thing analysts check.

**Caution**: incorrect registry edits can break the OS - always back up before editing (Registry -> File -> Export).

---

## 5. Event Viewer & Logs

Tool: `eventvwr.msc`

Main log categories:
- **Application** - events logged by applications
- **Security** - login attempts, privilege use, audit events (critical for security analysis)
- **System** - OS-level events (driver failures, service start/stop)

Key Event IDs to know (Security log):
| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | New user account created |
| 4732 | User added to a security-enabled group |

This is directly relevant to SOC/log analysis work later in the roadmap.

---

## Interview Questions

**Q1. Difference between NTFS permissions and Share permissions?**
NTFS permissions apply regardless of access method (local or network); Share permissions apply only over network access. When both apply, the most restrictive wins.

**Q2. What is the Registry?**
A hierarchical database storing OS and application configuration settings, accessed via `regedit`.

**Q3. What's the difference between a Service and a Scheduled Task?**
A Service runs continuously in the background independent of login; a Scheduled Task runs based on a specific trigger (time, event, login).

**Q4. What is Event ID 4625?**
A failed logon attempt - important for detecting brute-force attacks.

**Q5. Where would you check if you suspect a malicious account was created?**
Event Viewer -> Security log -> Event ID 4720 (account creation), and `net user`/`lusrmgr.msc` to verify current accounts.

## Key Takeaways
- Learned local user/group management tools and commands
- Understood NTFS vs Share permissions and how they combine
- Learned how to manage Services and Task Scheduler
- Understood Registry structure and its security relevance
- Learned key Event Viewer logs and Event IDs for security monitoring
