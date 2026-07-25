# Linux Commands Cheat Sheet

## Overview

Linux commands allow users to interact with the operating system through the command line. This cheat sheet provides a quick reference to the most commonly used commands for file management, process control, networking, permissions, package management, and system administration.

---

# Navigation

| Command | Description |
|----------|-------------|
| `pwd` | Show current directory |
| `ls` | List files and directories |
| `ls -l` | Detailed listing |
| `ls -la` | Show hidden files |
| `cd directory` | Change directory |
| `cd ..` | Go to parent directory |
| `cd ~` | Go to home directory |
| `clear` | Clear terminal screen |

---

# File Management

| Command | Description |
|----------|-------------|
| `touch file.txt` | Create an empty file |
| `mkdir folder` | Create a directory |
| `rmdir folder` | Remove an empty directory |
| `cp source destination` | Copy files or directories |
| `mv source destination` | Move or rename files |
| `rm file.txt` | Delete a file |
| `rm -r folder` | Delete a directory recursively |
| `find . -name file.txt` | Search for a file |
| `locate filename` | Find files using a database |

---

# Viewing Files

| Command | Description |
|----------|-------------|
| `cat file.txt` | Display file contents |
| `less file.txt` | View file page by page |
| `head file.txt` | Show first 10 lines |
| `tail file.txt` | Show last 10 lines |
| `tail -f logfile.log` | Monitor file updates |
| `tee output.txt` | Save and display output |

---

# Searching and Filtering

| Command | Description |
|----------|-------------|
| `grep "text" file.txt` | Search for text |
| `grep -r "text" .` | Recursive search |
| `sort file.txt` | Sort lines |
| `uniq file.txt` | Remove duplicate lines |
| `wc file.txt` | Count lines, words, and characters |

---

# Permissions

| Command | Description |
|----------|-------------|
| `chmod 755 file` | Change permissions |
| `chmod +x script.sh` | Make a script executable |
| `chown user file` | Change file owner |
| `chgrp group file` | Change file group |
| `umask` | Display default permissions |

---

# User Management

| Command | Description |
|----------|-------------|
| `whoami` | Show current user |
| `who` | Show logged-in users |
| `id` | Display user and group IDs |
| `groups` | Show group memberships |
| `passwd` | Change password |
| `useradd username` | Create a new user |
| `userdel username` | Delete a user |

---

# Process Management

| Command | Description |
|----------|-------------|
| `ps` | Display running processes |
| `ps aux` | Detailed process list |
| `top` | Real-time process monitor |
| `htop` | Interactive process viewer |
| `kill PID` | Terminate a process |
| `killall process` | Kill processes by name |
| `jobs` | Show background jobs |
| `bg` | Resume a background job |
| `fg` | Bring a job to the foreground |

---

# Disk Usage

| Command | Description |
|----------|-------------|
| `df -h` | Show disk usage |
| `du -sh folder` | Show directory size |
| `lsblk` | Display block devices |
| `mount` | List mounted filesystems |
| `umount` | Unmount a filesystem |

---

# Compression

| Command | Description |
|----------|-------------|
| `tar -cvf archive.tar folder` | Create tar archive |
| `tar -xvf archive.tar` | Extract tar archive |
| `zip archive.zip file` | Create ZIP archive |
| `unzip archive.zip` | Extract ZIP archive |
| `gzip file` | Compress a file |
| `gunzip file.gz` | Decompress a file |

---

# Networking

| Command | Description |
|----------|-------------|
| `ping host` | Test connectivity |
| `ip addr` | Show IP addresses |
| `hostname` | Display hostname |
| `curl URL` | Retrieve web content |
| `wget URL` | Download a file |
| `ssh user@host` | Connect via SSH |
| `scp file user@host:/path` | Securely copy files |
| `rsync` | Synchronize files |
| `ss -tuln` | Display listening ports |
| `netstat` | Show network connections |

---

# Package Management (APT)

| Command | Description |
|----------|-------------|
| `sudo apt update` | Update package index |
| `sudo apt upgrade` | Upgrade packages |
| `sudo apt install package` | Install a package |
| `sudo apt remove package` | Remove a package |
| `sudo apt autoremove` | Remove unused packages |
| `sudo apt search package` | Search for a package |

---

# System Information

| Command | Description |
|----------|-------------|
| `uname -a` | Kernel and system information |
| `hostnamectl` | Display system details |
| `uptime` | Show system uptime |
| `free -h` | Display memory usage |
| `lscpu` | Show CPU information |
| `lsmem` | Show memory information |
| `date` | Display current date and time |
| `history` | Show command history |

---

# Services

| Command | Description |
|----------|-------------|
| `systemctl status service` | View service status |
| `systemctl start service` | Start a service |
| `systemctl stop service` | Stop a service |
| `systemctl restart service` | Restart a service |
| `systemctl enable service` | Enable service at boot |
| `journalctl` | View system logs |

---

# Environment Variables

| Command | Description |
|----------|-------------|
| `env` | Display environment variables |
| `export VAR=value` | Create an environment variable |
| `echo $HOME` | Show home directory |
| `echo $PATH` | Show executable search path |
| `unset VAR` | Remove a variable |

---

# Redirection and Pipes

| Operator | Description |
|----------|-------------|
| `>` | Redirect output |
| `>>` | Append output |
| `<` | Redirect input |
| `2>` | Redirect errors |
| `|` | Pipe output to another command |

Examples:

```bash
ls > files.txt
cat file.txt | grep "Linux"
command >> output.log
```

---

# Useful Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Stop current command |
| `Ctrl + D` | Exit terminal |
| `Ctrl + L` | Clear screen |
| `Ctrl + R` | Search command history |
| `Ctrl + A` | Beginning of line |
| `Ctrl + E` | End of line |
| `Tab` | Auto-complete |
| `Ctrl + U` | Delete to beginning of line |
| `Ctrl + K` | Delete to end of line |

---

# Essential Linux Commands

```bash
pwd
ls -la
cd
mkdir
touch
cp
mv
rm
find
grep
cat
less
head
tail
chmod
chown
ps
top
kill
df
du
tar
zip
unzip
ping
curl
wget
ssh
scp
systemctl
journalctl
history
```

---

# Tips

- Use `Tab` for command and filename auto-completion.
- Use `history` to recall previous commands.
- Read command documentation with `man command`.
- Combine commands using pipes (`|`) for powerful workflows.
- Use `sudo` only when administrative privileges are required.

---

# Related Topics

- Bash Cheat Sheet
- Linux Commands
- Shell
- Shell Scripting
- File Management
- Process Management
- Networking
- System Administration