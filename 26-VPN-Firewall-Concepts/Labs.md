# Day 26 - Lab: VPN & NAT Configuration

## Objective
Set up a basic VPN connection and observe NAT behavior using available lab tools.

## Task 1: Set Up a Simple VPN (WireGuard - lightweight option)
```bash
sudo apt install wireguard -y
wg genkey | tee privatekey | wg pubkey > publickey
```
Create a basic config (`wg0.conf`) connecting two test machines/VMs, following WireGuard's quickstart documentation.

## Task 2: Verify VPN Tunnel
```bash
sudo wg-quick up wg0
wg show
ping <peer-vpn-ip>
```
Record: whether the tunnel established and ping succeeded over the VPN interface.

## Task 3: Observe NAT in Action
```bash
curl ifconfig.me        (shows your public IP)
ipconfig / ifconfig      (shows your private/internal IP)
```
Compare the two - the difference demonstrates NAT translating your private IP to a public one.

## Task 4: Cisco Packet Tracer - Configure PAT
1. Build topology: internal LAN + router + simulated "internet" cloud
2. Configure PAT on the router:
```
ip nat inside source list 1 interface gig0/0 overload
access-list 1 permit 192.168.1.0 0.0.0.255
interface gig0/1
 ip nat inside
interface gig0/0
 ip nat outside
```
3. Verify with `show ip nat translations`

## Results
| Item | Value |
|---|---|
| VPN tunnel established (Y/N) | |
| Ping over VPN successful (Y/N) | |
| Public IP observed | |
| Private IP observed | |
| PAT translation table entries | |

## Screenshots
```
![WireGuard Status](Screenshots/wireguard-status.png)
![NAT Translation Table](Screenshots/nat-translations.png)
```

## Lab Summary
Note the difference between your public and private IP, and how NAT/PAT made that translation possible.
