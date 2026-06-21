# Day 05 - Lab: AD Structure Exploration

## Objective
Set up or access a basic AD lab environment and explore its structure, users, groups, and authentication.

## Prerequisite
VirtualBox/VMware with a Windows Server VM (Server 2019/2022 evaluation edition, free from Microsoft), or use an existing lab if your college/work provides one.

## Task 1: Install AD DS Role (if setting up fresh)
On Windows Server:
1. Server Manager -> Add Roles and Features
2. Select "Active Directory Domain Services"
3. Promote server to Domain Controller
4. Create new forest, e.g., `lab.local`

## Task 2: Explore AD Structure
Open "Active Directory Users and Computers" (`dsa.msc`)
- Note default containers: Users, Computers, Domain Controllers
- Create a test OU: `Test-OU`
- Create a test user inside it: `lab-user1`
- Create a Security Group: `Lab-Admins`, add `lab-user1` to it

## Task 3: PowerShell AD Exploration
```powershell
Get-ADDomain
Get-ADForest
Get-ADUser -Filter * | Select Name
Get-ADGroup -Filter * | Select Name
Get-ADOrganizationalUnit -Filter * | Select Name
```

## Task 4: Observe Authentication Logs
On the Domain Controller, open Event Viewer -> Security log. Log in as `lab-user1` from a domain-joined client (or simulate locally) and find the corresponding logon event (Event ID 4624, look at Logon Type and Authentication Package fields - Kerberos vs NTLM).

## Results
| Item | Value |
|---|---|
| Forest/Domain name | |
| Test OU created (Y/N) | |
| Test user created (Y/N) | |
| Test group created (Y/N) | |
| Authentication package observed (Kerberos/NTLM) | |

## Screenshots
```
![AD Structure](Screenshots/ad-structure.png)
![PowerShell AD Query](Screenshots/ad-powershell.png)
![Logon Event](Screenshots/logon-event.png)
```

## Lab Summary
Note what surprised you about AD's default structure, and whether the authentication package was Kerberos or NTLM in your test.
