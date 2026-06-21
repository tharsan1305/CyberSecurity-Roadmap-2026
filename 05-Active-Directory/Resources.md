# Day 05 - Resources

## Tools Used
- Windows Server (evaluation edition, free from Microsoft)
- `dsa.msc` - Active Directory Users and Computers
- PowerShell AD module (`Get-ADUser`, `Get-ADGroup`, etc.)
- VirtualBox / VMware for lab VM

## Commands Reference
| Purpose | Command |
|---|---|
| View domain info | `Get-ADDomain` |
| View forest info | `Get-ADForest` |
| List all users | `Get-ADUser -Filter *` |
| List all groups | `Get-ADGroup -Filter *` |
| List all OUs | `Get-ADOrganizationalUnit -Filter *` |
| Create user | `New-ADUser -Name "name" -SamAccountName "user"` |

## Key Terms Glossary
- **KDC**: Key Distribution Center, issues Kerberos tickets, runs on the DC
- **TGT**: Ticket Granting Ticket, proves initial authentication
- **TGS**: Ticket Granting Service, issues Service Tickets
- **NTDS.dit**: the AD database file stored on Domain Controllers
- **Global Catalog**: a partial, searchable copy of all objects in the forest

## Further Reading
- Microsoft Learn: Active Directory Domain Services overview
- Microsoft Docs: Kerberos authentication overview

## Skills Gained Today
- AD structural navigation (Forest, Tree, Domain, OU)
- PowerShell AD module basics
- Understanding Kerberos vs NTLM authentication flow
- Trust and replication concepts
