# Day 26 - Resources

## Tools Used
- WireGuard (lightweight VPN)
- OpenVPN (reference, common enterprise alternative)
- Cisco Packet Tracer (NAT/PAT lab)

## Commands Reference
| Purpose | Command |
|---|---|
| Generate WireGuard keys | `wg genkey \| tee privatekey \| wg pubkey > publickey` |
| Bring up VPN tunnel | `sudo wg-quick up wg0` |
| Show VPN status | `wg show` |
| Check public IP | `curl ifconfig.me` |
| Cisco PAT config | `ip nat inside source list 1 interface <if> overload` |
| Show NAT translations (Cisco) | `show ip nat translations` |

## Key Terms Glossary
- **IKE**: Internet Key Exchange, negotiates security parameters for IPSec
- **ESP**: Encapsulating Security Payload, provides encryption in IPSec
- **Tunnel mode**: encrypts entire IP packet (site-to-site VPN)
- **Transport mode**: encrypts only payload (host-to-host)
- **PAT**: Port Address Translation, maps many private IPs to one public IP via ports

## Further Reading
- WireGuard official quickstart documentation (wireguard.com)
- Cisco documentation: NAT/PAT configuration guides
- Cloudflare Learning Center: What is a VPN

## Skills Gained Today
- VPN type selection (Site-to-Site vs Remote Access)
- IPSec vs SSL VPN distinction
- NAT/PAT configuration and verification
- Firewall least-privilege policy design
