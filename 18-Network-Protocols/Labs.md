# Day 18 - Lab: Network Protocols Observation

## Objective
Observe TCP handshakes, UDP traffic, and ICMP behavior using packet capture and command-line tools.

## Task 1: Capture a TCP Handshake with Wireshark
1. Install Wireshark (or use `tcpdump` on Linux if no GUI)
2. Start a capture on your active interface
3. Visit any website in a browser
4. Filter: `tcp.flags.syn == 1`
5. Find the SYN, SYN-ACK, ACK sequence for one connection

```bash
# Linux alternative using tcpdump
sudo tcpdump -i any -nn 'tcp[tcpflags] & (tcp-syn) != 0' -c 5
```

## Task 2: Observe UDP Traffic (DNS)
```bash
sudo tcpdump -i any -nn port 53 -c 5
```
In another terminal, trigger a DNS lookup:
```bash
nslookup example.com
```
Observe the UDP packet in the capture.

## Task 3: Test ICMP with Ping and Traceroute
```bash
ping -c 4 8.8.8.8
traceroute 8.8.8.8        (Linux)
tracert 8.8.8.8             (Windows)
```
Record: round-trip time (RTT) from ping, and number of hops from traceroute.

## Task 4: Identify Protocol/Port for Common Services
Using `netstat`/`ss`, identify which protocol (TCP/UDP) is used by services currently running on your machine.
```bash
ss -tulnp
```

## Results
| Item | Value |
|---|---|
| TCP handshake captured (Y/N) | |
| UDP DNS packet observed (Y/N) | |
| Ping average RTT | |
| Traceroute hop count | |
| TCP vs UDP services identified | |

## Screenshots
```
![TCP Handshake Capture](Screenshots/tcp-handshake.png)
![UDP DNS Capture](Screenshots/udp-dns.png)
![Traceroute Output](Screenshots/traceroute.png)
```

## Lab Summary
Note what surprised you seeing the handshake "live" versus just reading about it, and how many hops your traceroute showed.
