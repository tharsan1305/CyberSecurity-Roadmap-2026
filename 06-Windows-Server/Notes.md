# Day 06 - Windows Server

## Goal
Learn key Windows Server roles that support enterprise networks - DHCP, DNS, File/Print services, and Remote Desktop - building directly on the AD knowledge from Day 05.

---

## 1. Server Roles & Features

Windows Server uses "Roles" (major functions, e.g., AD DS, DNS, DHCP) and "Features" (supporting tools, e.g., .NET Framework, Backup) installed via Server Manager.

```powershell
# View installed roles/features
Get-WindowsFeature

# Install a role (example: DNS)
Install-WindowsFeature -Name DNS -IncludeManagementTools
```

## 2. DHCP Server

**DHCP (Dynamic Host Configuration Protocol)** automatically assigns IP addresses, subnet masks, gateways, and DNS servers to clients on the network - avoiding manual IP configuration.

DHCP process (DORA):
```
Discover  - client broadcasts looking for a DHCP server
Offer     - server offers an available IP
Request   - client requests that specific IP
Acknowledge - server confirms the lease
```

Key concepts:
- **Scope**: a range of IP addresses the DHCP server can assign
- **Lease**: how long a client can use an assigned IP before renewal is required
- **Reservation**: a specific IP permanently assigned to a specific MAC address

## 3. DNS Server

Windows Server can host DNS zones for internal name resolution (covered conceptually in Day 02, here applied to Windows Server administration).

Zone types:
- **Primary Zone**: the writable, authoritative copy of DNS records
- **Secondary Zone**: a read-only copy replicated from a primary zone (redundancy)
- **Forward Lookup Zone**: resolves names to IPs
- **Reverse Lookup Zone**: resolves IPs to names

```powershell
Add-DnsServerPrimaryZone -Name "lab.local" -ZoneFile "lab.local.dns"
Add-DnsServerResourceRecordA -ZoneName "lab.local" -Name "server1" -IPv4Address "192.168.1.10"
```

## 4. File & Print Services

**File Server Role**: centralizes file storage with shared folders, NTFS/Share permissions (from Day 03), and quota management.

**Print Server Role**: centralizes printer management, allowing clients to connect to shared printers rather than each having a direct connection.

## 5. Remote Desktop Services (RDS)

Allows users to remotely access a full desktop or specific applications hosted on the server.

Components:
- **RD Session Host**: hosts the desktop/app sessions
- **RD Gateway**: allows secure RDP access over HTTPS from outside the network
- **RD Connection Broker**: manages session load balancing across multiple RD hosts

Basic RDP connection: `mstsc` (Remote Desktop Connection client)

---

## Interview Questions

**Q1. What does DORA stand for in DHCP?**
Discover, Offer, Request, Acknowledge - the four-step process of a client obtaining an IP lease.

**Q2. Difference between a DHCP Scope and a Reservation?**
A Scope is a range of IPs available for assignment; a Reservation permanently assigns a specific IP to a specific MAC address within that scope.

**Q3. Difference between a Primary and Secondary DNS zone?**
Primary is the writable, authoritative copy; Secondary is a read-only replicated copy used for redundancy.

**Q4. What is RD Gateway used for?**
Allowing secure Remote Desktop access over HTTPS from outside the corporate network, without exposing RDP directly to the internet.

## Key Takeaways
- Learned Windows Server roles/features management
- Understood DHCP's DORA process, scopes, leases, and reservations
- Learned DNS zone types and basic DNS record management
- Learned File/Print server roles
- Understood Remote Desktop Services components
