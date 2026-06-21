# Day 03 - Lab: Windows Administration

## Objective
Practice user/group management, permissions, services, and event log review on a Windows machine (or VM).

## Task 1: User & Group Enumeration
```
net user
net localgroup
net localgroup administrators
```
Record: list of local users, list of local groups, members of Administrators.

## Task 2: Create a Test User and Group
```
net user testuser Pass@123 /add
net localgroup TestGroup /add
net localgroup TestGroup testuser /add
```
Verify with `net user testuser` and `net localgroup TestGroup`.

## Task 3: NTFS Permissions Check
1. Create a test folder
2. Right-click -> Properties -> Security tab
3. Note current permissions for your user account

## Task 4: Service Management
```
sc query wuauserv
sc query spooler
```
Open `services.msc`, find "Print Spooler", note its current status and startup type.

## Task 5: Event Viewer Review
1. Open `eventvwr.msc`
2. Navigate to Windows Logs -> Security
3. Filter for Event ID 4624 (successful logons) and 4625 (failed logons)
Record: how many of each in the last 24 hours.

## Results Table
| Item | Value |
|---|---|
| Local users found | |
| Local groups found | |
| Test user created (Y/N) | |
| Print Spooler status | |
| Event ID 4624 count | |
| Event ID 4625 count | |

## Cleanup
```
net user testuser /delete
net localgroup TestGroup /delete
```

## Screenshots
Save in `Screenshots/`:
```
![User List](Screenshots/user-list.png)
![NTFS Permissions](Screenshots/ntfs-permissions.png)
![Event Viewer](Screenshots/event-viewer.png)
```

## Lab Summary
Write 2-3 lines on what you found in your Event Viewer logs and any surprises in your local user/group setup.
