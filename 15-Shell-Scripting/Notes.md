# Day 15 - Shell Scripting

## Goal
Learn Bash scripting to automate repetitive Linux tasks - a core skill for system administration, DevOps, and security automation.

---

## 1. Bash Syntax

```bash
#!/bin/bash
# This is a comment

echo "Hello, World!"
```

Make executable and run:
```bash
chmod +x script.sh
./script.sh
```

## 2. Variables & Loops

```bash
# Variables (no spaces around =)
name="Tharsan"
echo "Hello, $name"

# Command substitution
current_date=$(date)
echo "Today is $current_date"

# For loop
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# For loop over files
for file in /var/log/*.log; do
    echo "Found log: $file"
done

# While loop
count=0
while [ $count -lt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done
```

## 3. Conditionals

```bash
#!/bin/bash
read -p "Enter a number: " num

if [ $num -gt 10 ]; then
    echo "Greater than 10"
elif [ $num -eq 10 ]; then
    echo "Equal to 10"
else
    echo "Less than 10"
fi
```

Common test operators:
```
-eq  equal           -gt  greater than
-ne  not equal        -lt  less than
-f   file exists        -d  directory exists
```

## 4. Functions

```bash
greet() {
    local name=$1
    echo "Hello, $name!"
}

greet "Tharsan"

# Function with return value
add() {
    echo $(($1 + $2))
}

result=$(add 5 3)
echo "Sum: $result"
```

## 5. Automation Scripts

Example: a disk space monitoring script that alerts if usage is too high.
```bash
#!/bin/bash
THRESHOLD=80
USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')

if [ $USAGE -gt $THRESHOLD ]; then
    echo "WARNING: Disk usage is at ${USAGE}%"
else
    echo "Disk usage OK: ${USAGE}%"
fi
```

Example: a simple backup automation script.
```bash
#!/bin/bash
BACKUP_DIR="/backups"
SOURCE_DIR="/etc"
DATE=$(date +%Y%m%d)

mkdir -p $BACKUP_DIR
tar -czf "$BACKUP_DIR/etc_backup_$DATE.tar.gz" $SOURCE_DIR
echo "Backup completed: etc_backup_$DATE.tar.gz"
```

---

## Interview Questions

**Q1. How do you make a shell script executable?**
`chmod +x script.sh`, then run it with `./script.sh`

**Q2. What's the difference between `=` and `-eq` in Bash conditionals?**
`=` is used for string comparison; `-eq` is used for numeric comparison.

**Q3. How do you capture command output into a variable?**
Using command substitution: `variable=$(command)`

**Q4. Why is shell scripting valuable for security/sysadmin work?**
It automates repetitive tasks (backups, monitoring, log parsing) directly using native OS tools, without needing a separate programming environment.

## Key Takeaways
- Learned Bash script structure and execution
- Learned variables, command substitution, and loops
- Learned conditional statements and test operators
- Learned function definition with parameters and return values
- Built two practical automation scripts: disk monitoring and backup
