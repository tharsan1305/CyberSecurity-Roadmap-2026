# Day 67 - Resources

## Tools Used
- Linux command-line: grep, awk, sort, uniq, cut
- tail, journalctl (for live log analysis)

## Commands Reference
| Purpose | Command |
|---|---|
| Search for failed logins | `grep "Failed password" /var/log/auth.log` |
| Count per IP | `awk '{print $IP_FIELD}' \| sort \| uniq -c \| sort -rn` |
| Live log follow | `tail -f /var/log/auth.log` |
| Windows Security log (PowerShell) | `Get-WinEvent -LogName Security -MaxEvents 100` |

## Key Terms Glossary
- **Syslog**: traditional Unix log format
- **CEF**: Common Event Format for security tool logs
- **Anomaly**: a deviation from established baseline behavior
- **Correlation**: connecting related events across sources or time

## Further Reading
- SANS Reading Room: Log Management and Analysis guides (free)

## Skills Gained Today
- Log source identification and format understanding
- Command-line log parsing for security event extraction
- Brute force pattern detection from log data
