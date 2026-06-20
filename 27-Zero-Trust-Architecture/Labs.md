# Day 27 - Lab: Zero Trust Concepts (Research + Design Exercise)

## Objective
Since Zero Trust is primarily an architectural/conceptual framework (not a single tool to install), this lab is a design and research exercise rather than a hands-on technical lab.

## Task 1: Research a Real Zero Trust Implementation
Research how one major vendor implements Zero Trust (pick one):
- Google BeyondCorp
- Microsoft Zero Trust (Entra ID Conditional Access)
- Cloudflare Zero Trust

Write a summary covering: what problem it solves, key components, how identity verification works in their model.

## Task 2: Design Exercise - Segment a Sample Network
Given this flat network:
```
[All devices on 192.168.1.0/24]
- HR Workstations
- Finance Workstations
- Finance Database Server
- Guest WiFi devices
- IT Admin Workstations
```

Redesign it using micro-segmentation principles. Define:
- What segments/VLANs you'd create
- What access each segment should have to others (a simple access matrix)
- Which segment should NEVER directly reach the Finance Database Server

## Task 3: Conditional Access Policy Design
Write a sample Zero Trust access policy in plain language for: "A finance employee accessing the finance database server."

Example structure:
```
IF user.role == "Finance" 
AND device.compliance == "Healthy" 
AND location == "Corporate Network OR Approved VPN"
AND mfa_verified == True
THEN allow access to Finance DB
ELSE deny / require additional verification
```

## Results
| Item | Value |
|---|---|
| Vendor researched | |
| Number of segments designed | |
| Segment most restricted | |
| Access policy written (Y/N) | |

## Lab Summary
Write 3-4 lines on how this exercise changes your view of "trusted internal network" thinking, and one real-world scenario where Zero Trust would have prevented a breach (research a known incident if helpful).
