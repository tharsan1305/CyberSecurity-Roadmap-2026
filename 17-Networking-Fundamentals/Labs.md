# Day 17 - Lab: Networking Fundamentals

## Objective
Practice identifying IP classes, inspecting active ports, and mapping OSI layers to real traffic.

## Task 1: Identify Your Own Network Config
```
ipconfig /all      (Windows)
ip addr               (Linux)
```
Record: your IP address, subnet mask, default gateway, and whether your IP falls in a private range.

## Task 2: Check Active Ports/Connections
```
netstat -ano          (Windows)
ss -tulnp               (Linux, modern replacement for netstat)
```
Record: 5 active listening ports and the services associated with them.

## Task 3: Map Common Ports
Without looking it up, try to recall the port number for: HTTP, HTTPS, SSH, FTP, DNS, RDP. Then verify against the reference table and note which ones you got right.

## Task 4: Visualize OSI Layers with a Real Request
Using browser DevTools (from Day 02) on any HTTPS website:
1. Open Network tab, reload the page
2. Identify what's happening at each rough layer:
   - Application: the HTTP request/response itself
   - Presentation: the TLS/SSL encryption (check the padlock/certificate)
   - Transport: note the destination port (443)
   - Network: note the destination IP

## Results
| Item | Value |
|---|---|
| Your IP address | |
| Private range? (Y/N) | |
| Default gateway | |
| Listening ports found | |
| Ports correctly recalled | /6 |

## Screenshots
```
![IP Config](Screenshots/ip-config.png)
![Active Ports](Screenshots/active-ports.png)
```

## Lab Summary
Note which OSI layer concept felt most abstract before mapping it to a real browser request, and whether that exercise made it clearer.
