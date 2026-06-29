# Day 61 - Resources

## Tools Used
- Nmap, Metasploit Framework (msfconsole)
- Metasploitable2 (target VM)

## Commands Reference
| Purpose | Command |
|---|---|
| Full service scan | `nmap -sV -sC -O <target>` |
| Launch Metasploit | `msfconsole` |
| Search for exploit | `search <keyword>` |
| Use an exploit | `use <exploit-path>` |
| Set target | `set RHOSTS <ip>` |
| Run exploit | `run` / `exploit` |

## Key Terms Glossary
- **PTES**: Penetration Testing Execution Standard
- **Meterpreter**: Metasploit's advanced post-exploitation shell
- **Lateral Movement**: moving from one compromised system to others within scope

## Further Reading
- ptes.org (official PTES documentation)
- Offensive Security's PWK/PEN-200 course (the gold standard for practical pentesting)

## Skills Gained Today
- End-to-end PTES methodology execution
- Metasploit basics for lab exploitation
- Professional pentest report writing
