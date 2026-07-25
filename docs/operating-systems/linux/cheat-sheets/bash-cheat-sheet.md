# Bash Cheat Sheet

## Overview

Bash (Bourne Again SHell) is the default command-line shell for most Linux distributions. It allows users to execute commands, automate tasks with scripts, manage files, and control system operations.

This cheat sheet provides a quick reference to commonly used Bash commands, shortcuts, variables, scripting syntax, and operators.

---

# Basic Commands

| Command | Description |
|----------|-------------|
| `pwd` | Print current directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `touch` | Create an empty file |
| `cp` | Copy files/directories |
| `mv` | Move or rename files |
| `rm` | Remove files/directories |
| `clear` | Clear terminal screen |
| `history` | Show command history |
| `exit` | Exit the shell |

---

# File Operations

```bash
ls -l
ls -la
cp file1 file2
mv old.txt new.txt
rm file.txt
rm -r folder/
touch notes.txt
mkdir projects
```

---

# Viewing File Contents

```bash
cat file.txt
less file.txt
head file.txt
tail file.txt
tail -f logfile.log
```

---

# Searching

```bash
find . -name "*.txt"
grep "error" logfile.log
grep -r "main" .
locate filename
```

---

# Permissions

```bash
chmod 755 script.sh
chmod +x script.sh
chown user:file file.txt
chgrp developers file.txt
```

---

# Process Management

```bash
ps
ps aux
top
kill PID
killall firefox
jobs
bg
fg
```

---

# Networking

```bash
ping google.com
ip addr
hostname
curl https://example.com
wget URL
ssh user@host
scp file.txt user@host:/tmp
ss -tuln
```

---

# Package Management (APT)

```bash
sudo apt update
sudo apt upgrade
sudo apt install package
sudo apt remove package
sudo apt autoremove
```

---

# Environment Variables

Display variable:

```bash
echo $HOME
```

Create variable:

```bash
NAME="Linux"
```

Export variable:

```bash
export NAME
```

List variables:

```bash
env
```

Unset variable:

```bash
unset NAME
```

---

# Redirection

Overwrite file:

```bash
command > file.txt
```

Append to file:

```bash
command >> file.txt
```

Read from file:

```bash
command < file.txt
```

Redirect errors:

```bash
command 2> error.log
```

Redirect output and errors:

```bash
command > output.log 2>&1
```

Discard output:

```bash
command > /dev/null
```

---

# Pipes

```bash
ls -l | grep ".txt"
cat file.txt | less
ps aux | grep nginx
history | tail
```

---

# Wildcards

| Wildcard | Meaning |
|-----------|---------|
| `*` | Matches any number of characters |
| `?` | Matches one character |
| `[abc]` | Matches one listed character |
| `[0-9]` | Matches a digit |

Examples:

```bash
ls *.txt
rm file?.txt
```

---

# Command Substitution

```bash
echo $(date)
```

Old syntax:

```bash
echo `date`
```

---

# Variables

```bash
USER="John"
echo "$USER"
```

Read user input:

```bash
read name
echo "$name"
```

---

# Arithmetic

```bash
echo $((5 + 3))
```

Increment:

```bash
((count++))
```

---

# Conditional Statements

```bash
if [ "$age" -ge 18 ]; then
    echo "Adult"
fi
```

---

# Comparison Operators

## Numeric

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-lt` | Less than |
| `-le` | Less than or equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |

---

## String

| Operator | Meaning |
|----------|---------|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | Empty string |
| `-n` | Not empty |

---

# Loops

## For Loop

```bash
for file in *.txt
do
    echo "$file"
done
```

## While Loop

```bash
while read line
do
    echo "$line"
done < file.txt
```

---

# Functions

```bash
greet() {
    echo "Hello!"
}

greet
```

---

# Arrays

Create array:

```bash
colors=("red" "green" "blue")
```

Access element:

```bash
echo "${colors[0]}"
```

All elements:

```bash
echo "${colors[@]}"
```

---

# Useful Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Stop current command |
| `Ctrl + D` | Exit shell |
| `Ctrl + L` | Clear screen |
| `Ctrl + R` | Search history |
| `Ctrl + A` | Beginning of line |
| `Ctrl + E` | End of line |
| `Ctrl + U` | Delete to beginning |
| `Ctrl + K` | Delete to end |
| `Ctrl + W` | Delete previous word |
| `Tab` | Auto-complete |

---

# Bash Script Template

```bash
#!/bin/bash

echo "Hello, World!"
```

Make executable:

```bash
chmod +x script.sh
```

Run:

```bash
./script.sh
```

---

# Useful Special Variables

| Variable | Description |
|----------|-------------|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$$` | Process ID |
| `$?` | Exit status of last command |
| `$HOME` | Home directory |
| `$PWD` | Current directory |
| `$PATH` | Executable search path |

---

# Common Bash Operators

| Operator | Description |
|----------|-------------|
| `&&` | Execute next command if previous succeeds |
| `||` | Execute next command if previous fails |
| `;` | Execute commands sequentially |
| `|` | Pipe output |
| `>` | Redirect output |
| `>>` | Append output |
| `<` | Redirect input |

---

# Tips

- Use `Tab` for auto-completion.
- Use `history` to view previous commands.
- Quote variables using `" "` to avoid word-splitting.
- Use `man command` to read documentation.
- Test scripts with `bash -n script.sh`.
- Debug scripts with `bash -x script.sh`.

---

# Related Topics

- Shell
- Shell Scripting
- Linux Commands
- Environment Variables
- Process Management
- File Management
- Permissions
- Bash