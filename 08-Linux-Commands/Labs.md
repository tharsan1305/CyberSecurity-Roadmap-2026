# Day 08 - Lab: Linux Commands Practice

## Task 1: File Operations
```bash
mkdir testlab && cd testlab
touch file1.txt file2.txt
cp file1.txt file1_copy.txt
mv file2.txt renamed.txt
find / -name "*.conf" 2>/dev/null | head -10
```

## Task 2: Permissions Practice
```bash
touch script.sh
chmod 755 script.sh
ls -la script.sh
chown $(whoami):$(whoami) script.sh
```
Record the permission string shown by `ls -la`.

## Task 3: Process Management
```bash
ps aux | head -10
top -n 1
sleep 100 &
ps aux | grep sleep
kill -9 <pid-of-sleep>
```

## Task 4: Text Processing on a Log File
```bash
# Generate a sample log
echo -e "INFO: started\nERROR: failed login\nINFO: ok\nERROR: timeout" > sample.log

grep "ERROR" sample.log
awk '{print $1}' sample.log
sed 's/ERROR/WARNING/g' sample.log
```

## Task 5: Networking Commands
```bash
ip addr
ping -c 4 8.8.8.8
curl -I https://www.google.com
```

## Results
| Item | Value |
|---|---|
| Files created | |
| Permission string after chmod 755 | |
| Sleep process killed (Y/N) | |
| ERROR lines found in log | |
| Ping success (Y/N) | |

## Screenshots
```
![File Operations](Screenshots/file-ops.png)
![Permissions](Screenshots/permissions.png)
![Grep Output](Screenshots/grep-output.png)
```

## Lab Summary
Note which command felt most useful and which syntax was hardest to remember (grep/awk/sed are commonly tricky at first).
