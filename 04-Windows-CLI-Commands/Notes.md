# Day 04 - Windows CLI Commands

## Goal
Build fluency in CMD and PowerShell - essential for administration, automation, and incident response on Windows systems.

## 1. CMD Commands

### Navigation & File Operations
```
dir                  list directory contents
cd <path>            change directory
copy <src> <dst>     copy file
move <src> <dst>     move file
del <file>           delete file
mkdir <name>         create directory
```

### System & Network Info
```
ipconfig /all        full network configuration
netstat -ano          active connections with PID
tasklist               list running processes
systeminfo             full system information
```

### Process Control
```
taskkill /PID <pid> /F     force kill process by PID
taskkill /IM <name> /F     force kill process by name
```

## 2. PowerShell

PowerShell is object-oriented (outputs objects, not just text), making it far more powerful than CMD for scripting and automation.

### Common Cmdlets
```
Get-Process                  list running processes
Get-Service                  list services
Get-ChildItem                 list directory contents (like dir/ls)
Get-Content <file>            read file contents
Get-EventLog Security -Newest 20    view recent security events
```

### Scripting Basics
```powershell
$name = "Tharsan"
Write-Output "Hello $name"

if ($condition) {
    Write-Output "True branch"
} else {
    Write-Output "False branch"
}

foreach ($item in $list) {
    Write-Output $item
}
```

### Remote Management (WinRM)
```powershell
Enter-PSSession -ComputerName <hostname>
Invoke-Command -ComputerName <hostname> -ScriptBlock { Get-Process }
```
WinRM must be enabled on the target (`winrm quickconfig`) and proper permissions/firewall rules in place.

## Interview Questions

**Q1. Difference between CMD and PowerShell?**
CMD processes text; PowerShell processes objects, enabling far more powerful scripting, filtering, and automation.

**Q2. How do you forcefully kill a process by PID?**
`taskkill /PID <pid> /F`

**Q3. What cmdlet lists running services in PowerShell?**
`Get-Service`

**Q4. What does `netstat -ano` show?**
All active network connections along with the Process ID (PID) using each connection.

## Key Takeaways
- Learned core CMD commands for navigation, system info, and process control
- Learned PowerShell cmdlets and basic scripting (variables, conditionals, loops)
- Understood remote management via WinRM
