# Day 15 - Resources

## Tools Used
- Bash (default shell on most Linux distros)

## Commands/Syntax Reference
| Purpose | Syntax |
|---|---|
| Shebang line | `#!/bin/bash` |
| Make executable | `chmod +x script.sh` |
| Variable assignment | `name="value"` (no spaces around =) |
| Command substitution | `result=$(command)` |
| For loop | `for i in list; do ... done` |
| While loop | `while [ condition ]; do ... done` |
| If statement | `if [ condition ]; then ... fi` |
| Function | `name() { ... }` |
| Read user input | `read -p "prompt" variable` |

## Test Operators Reference
| Operator | Meaning |
|---|---|
| `-eq` / `-ne` | numeric equal / not equal |
| `-gt` / `-lt` | greater than / less than |
| `-f` | file exists |
| `-d` | directory exists |
| `-z` | string is empty |

## Further Reading
- ShellCheck (shellcheck.net) - free linter that catches common Bash mistakes
- Bash Guide for Beginners (tldp.org)
- explainshell.com - paste any command for a breakdown

## Skills Gained Today
- Bash script structure and execution
- Variables, loops, conditionals, functions
- Practical automation scripts: disk monitoring, backups, security log analysis
