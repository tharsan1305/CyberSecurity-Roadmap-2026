# Day 06 - Resources

## Tools Used
- Windows Server (evaluation edition)
- `dhcpmgmt.msc` - DHCP console
- `dnsmgmt.msc` - DNS console
- PowerShell DHCP/DNS Server modules

## Commands Reference
| Purpose | Command |
|---|---|
| Install role | `Install-WindowsFeature -Name <RoleName> -IncludeManagementTools` |
| View installed roles | `Get-WindowsFeature` |
| Create DNS zone | `Add-DnsServerPrimaryZone -Name "domain" -ZoneFile "file.dns"` |
| Add DNS A record | `Add-DnsServerResourceRecordA -ZoneName "domain" -Name "host" -IPv4Address "ip"` |
| Release/renew IP (client) | `ipconfig /release` then `ipconfig /renew` |

## Key Terms Glossary
- **DORA**: Discover, Offer, Request, Acknowledge (DHCP process)
- **Scope**: DHCP IP address range available for lease
- **Lease**: time period a client retains an assigned IP
- **RD Gateway**: secure HTTPS-based remote desktop access point

## Further Reading
- Microsoft Learn: DHCP and DNS Server role documentation
- Microsoft Docs: Remote Desktop Services architecture

## Skills Gained Today
- DHCP role installation and scope configuration
- DNS role installation, zone creation, and record management
- File sharing with NTFS permissions
- Remote Desktop Services component understanding
