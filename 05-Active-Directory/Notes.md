# Day 05 (Part 1 of 3) - Active Directory: Structure & Authentication

## Goal
Understand AD's logical structure and authentication mechanisms - foundational before AD Pentesting (Topic 66). Active Directory is a big topic, split across 3 days.

---

## 1. What is Active Directory?
A directory service for Windows domain networks - centralizes management of users, computers, groups, and resources.

## 2. Domain & Forest Structure

- **Domain**: a logical group of objects (users, computers) sharing a common AD database and security policies
- **Tree**: a collection of domains sharing a contiguous namespace (e.g., corp.com, hr.corp.com)
- **Forest**: a collection of one or more trees, the top-level container, sharing a common schema and global catalog

```
Forest
└── Tree (corp.com)
    ├── Domain: corp.com
    └── Domain: hr.corp.com (child domain)
```

## 3. Users, Groups, OUs

- **User objects**: represent people/accounts that can authenticate
- **Computer objects**: represent machines joined to the domain
- **Groups**: collections of users/computers for permission assignment
  - Security Groups (for permissions)
  - Distribution Groups (for email lists only, no security use)
- **OU (Organizational Unit)**: container used to organize objects and apply Group Policy at a granular level

Group scopes:
- **Domain Local**: used to assign permissions within the same domain
- **Global**: used across the domain, can be used in other domains' ACLs
- **Universal**: used across the entire forest

## 4. Domain Controller (DC)
A server running AD Domain Services, holding the AD database (NTDS.dit) and handling authentication requests.

## 5. Authentication: Kerberos & NTLM

### Kerberos (modern, default in AD)
Ticket-based authentication protocol. Simplified flow:
```
1. User logs in -> requests TGT (Ticket Granting Ticket) from KDC (Key Distribution Center, runs on DC)
2. User presents TGT to request a Service Ticket for a specific resource
3. User presents Service Ticket to the target server to gain access
```
Key components: KDC, TGT, TGS (Ticket Granting Service), Service Tickets.

### NTLM (legacy, still used for backward compatibility)
Challenge-response authentication protocol, older and less secure than Kerberos. Still relevant because:
- Used when Kerberos isn't available (e.g., accessing by IP instead of hostname)
- A common target in AD attacks (Pass-the-Hash, relay attacks - covered in Topic 66)

## 6. Trusts & Replication

**Trust**: allows users in one domain to access resources in another domain.
- One-way trust: Domain A trusts Domain B (B's users can access A's resources, not vice versa)
- Two-way trust: mutual access

**Replication**: AD data is replicated between Domain Controllers to keep them in sync, using a multi-master model (any DC can accept changes, which then propagate to others).

---

## Interview Questions

**Q1. What is the difference between a Domain and a Forest?**
A Domain is a single management boundary; a Forest is the top-level container holding one or more domain trees that share a common schema.

**Q2. What is an OU used for?**
Organizing AD objects and applying Group Policy at a granular level.

**Q3. Explain the basic Kerberos authentication flow.**
User authenticates and receives a TGT from the KDC, then uses the TGT to request Service Tickets for specific resources, which are presented to access those resources.

**Q4. Why is NTLM still relevant in security discussions?**
It's older/weaker than Kerberos and is a frequent target for attacks like Pass-the-Hash and NTLM relay, even though Kerberos is the modern default.

**Q5. What is a Domain Controller?**
A server that hosts AD Domain Services and handles authentication for the domain.

## Key Takeaways
- Understood AD's hierarchical structure: Forest -> Tree -> Domain -> OU
- Learned group scopes: Domain Local, Global, Universal
- Learned Kerberos authentication flow (TGT, KDC, Service Tickets)
- Understood why NTLM remains security-relevant despite being legacy
- Learned Trust types and replication basics
