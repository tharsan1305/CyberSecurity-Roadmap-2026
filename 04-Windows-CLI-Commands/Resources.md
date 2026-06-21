# Day 04 - Resources

## Commands Reference
| Purpose | CMD | PowerShell |
|---|---|---|
| List processes | `tasklist` | `Get-Process` |
| List services | `sc query` | `Get-Service` |
| List directory | `dir` | `Get-ChildItem` |
| Kill process | `taskkill /PID <pid> /F` | `Stop-Process -Id <pid>` |
| Network connections | `netstat -ano` | `Get-NetTCPConnection` |
| Read file | `type <file>` | `Get-Content <file>` |

## Key Terms
- **Cmdlet**: PowerShell command (Verb-Noun format, e.g., Get-Process)
- **PID**: Process ID, unique identifier for a running process
- **WinRM**: Windows Remote Management, protocol for remote PowerShell sessions

## Further Reading
- Microsoft Learn: PowerShell scripting basics
- SS64.com CMD and PowerShell command reference

## Skills Gained
- CMD navigation and system inspection
- PowerShell cmdlets and basic scripting
- Process management and remote session basics
