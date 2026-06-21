# Day 03 - Resources

## Tools Used
- `lusrmgr.msc` - Local Users and Groups
- `compmgmt.msc` - Computer Management
- `services.msc` - Services console
- `taskschd.msc` - Task Scheduler
- `regedit` - Registry Editor
- `eventvwr.msc` - Event Viewer

## Commands Reference
| Purpose | Command |
|---|---|
| List local users | `net user` |
| View user details | `net user <username>` |
| List local groups | `net localgroup` |
| View group members | `net localgroup <groupname>` |
| Add user | `net user <username> <password> /add` |
| Add group | `net localgroup <groupname> /add` |
| Add user to group | `net localgroup <groupname> <username> /add` |
| Delete user | `net user <username> /delete` |
| Query service status | `sc query <servicename>` |
| Start/stop service | `sc start/stop <servicename>` |

## Key Event IDs (Security Log)
| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4732 | User added to security group |
| 4634 | Logoff |
| 4648 | Logon using explicit credentials |

## Further Reading
- Microsoft Learn: Windows Server Administration fundamentals
- Microsoft Docs: Security audit events reference

## Skills Gained Today
- Local user/group administration
- NTFS vs Share permission concepts
- Service and scheduled task management
- Registry structure awareness
- Security event log analysis basics
