# Day 08 - Resources

## Commands Reference
| Purpose | Command |
|---|---|
| List files (detailed) | `ls -la` |
| Copy file | `cp src dst` |
| Move/rename file | `mv src dst` |
| Remove file/folder | `rm file` / `rm -rf folder` |
| Find files | `find / -name "pattern"` |
| Change permissions | `chmod <octal> file` |
| Change owner | `chown user:group file` |
| List processes | `ps aux` |
| Live monitor | `top` |
| Kill process | `kill <pid>` / `kill -9 <pid>` |
| Search text pattern | `grep "pattern" file` |
| Print columns | `awk '{print $N}' file` |
| Find/replace text | `sed 's/old/new/g' file` |
| Show IP config | `ip addr` |
| Test connectivity | `ping -c 4 <host>` |

## Key Terms Glossary
- **Octal permission notation**: numeric representation of rwx permissions (r=4, w=2, x=1)
- **PID**: Process ID
- **SIGKILL (-9)**: forceful, non-graceful process termination signal
- **Pipe (`|`)**: chains command output as input to the next command

## Further Reading
- explainshell.com (paste any command to see a breakdown)
- Linux man pages: `man grep`, `man awk`, `man sed`, `man chmod`

## Skills Gained Today
- File operations and permission management
- Process management and monitoring
- Text processing with grep/awk/sed
- Basic networking command usage
