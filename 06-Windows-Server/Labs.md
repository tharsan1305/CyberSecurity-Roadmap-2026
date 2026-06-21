# Day 06 - Lab: Windows Server Roles

## Objective
Install and configure DHCP and DNS roles on a Windows Server VM, and test client connectivity.

## Task 1: Install DHCP Role
```powershell
Install-WindowsFeature -Name DHCP -IncludeManagementTools
```
Configure a scope via DHCP console (`dhcpmgmt.msc`):
- Scope range: e.g., 192.168.1.100 - 192.168.1.200
- Subnet mask, default gateway, DNS server

## Task 2: Test DHCP from a Client VM
Connect a client VM to the same virtual network, set it to obtain IP automatically, and verify:
```
ipconfig /all
ipconfig /release
ipconfig /renew
```
Record the IP address leased from your DHCP scope.

## Task 3: Install DNS Role and Create a Zone
```powershell
Install-WindowsFeature -Name DNS -IncludeManagementTools
Add-DnsServerPrimaryZone -Name "lab.local" -ZoneFile "lab.local.dns"
Add-DnsServerResourceRecordA -ZoneName "lab.local" -Name "server1" -IPv4Address "192.168.1.10"
```
Test resolution from client: `nslookup server1.lab.local`

## Task 4: Set Up a File Share
1. Create a folder, share it (`Properties -> Sharing`)
2. Set NTFS permissions for a test user
3. Access from a client: `\\<server-ip>\<sharename>`

## Results
| Item | Value |
|---|---|
| DHCP scope configured (Y/N) | |
| Client received IP from scope (Y/N) | |
| DNS zone created (Y/N) | |
| nslookup resolved correctly (Y/N) | |
| File share accessible from client (Y/N) | |

## Screenshots
```
![DHCP Scope](Screenshots/dhcp-scope.png)
![DNS Zone](Screenshots/dns-zone.png)
![File Share Access](Screenshots/file-share.png)
```

## Lab Summary
Note any issues getting the client to receive a DHCP lease or resolve DNS, and how you troubleshot them.
