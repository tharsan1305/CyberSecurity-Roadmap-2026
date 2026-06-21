# Day 04 - Lab: CLI Practice

## Task 1: CMD System Info
```
ipconfig /all
systeminfo
tasklist
netstat -ano
```
Record your IP address, OS build, and top 3 processes by familiarity.

## Task 2: Process Management
1. Open Notepad
2. Find its PID: `tasklist | findstr Notepad`
3. Kill it: `taskkill /PID <pid> /F`

## Task 3: PowerShell Basics
```powershell
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5
Get-Service | Where-Object {$_.Status -eq "Running"}
Get-EventLog Security -Newest 10
```
Record: top 5 CPU-consuming processes, count of running services.

## Task 4: Simple PowerShell Script
Create `test.ps1`:
```powershell
$services = Get-Service | Where-Object {$_.Status -eq "Stopped"}
Write-Output "Stopped services count: $($services.Count)"
```
Run with: `powershell -ExecutionPolicy Bypass -File test.ps1`

## Results
| Item | Value |
|---|---|
| IP Address | |
| Notepad PID killed (Y/N) | |
| Top CPU process | |
| Running services count | |
| Stopped services count | |

## Screenshots
```
![Tasklist Output](Screenshots/tasklist.png)
![PowerShell Script Run](Screenshots/ps-script.png)
```

## Lab Summary
Note what was harder - CMD or PowerShell - and why.
