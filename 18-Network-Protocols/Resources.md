# Day 18 - Resources

## Tools Used
- Wireshark (packet capture and analysis, GUI)
- tcpdump (command-line packet capture, Linux)
- ping, traceroute/tracert, nslookup

## Commands Reference
| Purpose | Command |
|---|---|
| Capture TCP SYN packets | `tcpdump -i any 'tcp[tcpflags] & (tcp-syn) != 0'` |
| Capture DNS (port 53) | `tcpdump -i any port 53` |
| Ping a host | `ping -c 4 <host>` |
| Trace route (Linux) | `traceroute <host>` |
| Trace route (Windows) | `tracert <host>` |
| List listening sockets | `ss -tulnp` |

## Key Terms Glossary
- **Three-Way Handshake**: SYN, SYN-ACK, ACK sequence establishing a TCP connection
- **TTL**: Time To Live, decremented at each hop; used by traceroute to map paths
- **RTT**: Round-Trip Time, how long a packet takes to reach destination and return

## Further Reading
- Wireshark official documentation and sample captures
- Cloudflare Learning Center: What is TCP / What is UDP / What is ICMP

## Skills Gained Today
- Packet capture with Wireshark/tcpdump
- Direct observation of TCP handshake and UDP traffic
- ICMP-based diagnostics (ping, traceroute)
- Protocol-to-port mapping for common services
