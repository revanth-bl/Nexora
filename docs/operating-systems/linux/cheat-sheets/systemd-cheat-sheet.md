# System Administration Cheat Sheet

## Overview

System administration involves managing Linux systems to ensure they are secure, reliable, and efficient. This cheat sheet provides a quick reference to essential commands for user management, services, packages, storage, monitoring, networking, security, and system maintenance.

---

# System Information

| Command | Description |
|----------|-------------|
| `uname -a` | Display kernel and system information |
| `hostnamectl` | Show hostname and OS details |
| `uptime` | Show system uptime and load |
| `date` | Display current date and time |
| `whoami` | Show current user |
| `who` | Show logged-in users |
| `id` | Display user and group IDs |
| `history` | Show command history |

---

# User Management

Create a user:

```bash
sudo useradd username
```

Set password:

```bash
sudo passwd username
```

Delete user:

```bash
sudo userdel username
```

Delete user and home directory:

```bash
sudo userdel -r username
```

Modify user:

```bash
sudo usermod
```

Create group:

```bash
sudo groupadd developers
```

View groups:

```bash
groups username
```

---

# Package Management

## APT (Debian/Ubuntu)

```bash
sudo apt update
sudo apt upgrade
sudo apt install package
sudo apt remove package
sudo apt autoremove
sudo apt search package
```

## DNF (Fedora)

```bash
sudo dnf install package
sudo dnf remove package
sudo dnf update
```

## YUM (RHEL/CentOS)

```bash
sudo yum install package
sudo yum update
```

---

# Service Management

Check service status:

```bash
systemctl status nginx
```

Start service:

```bash
sudo systemctl start nginx
```

Stop service:

```bash
sudo systemctl stop nginx
```

Restart service:

```bash
sudo systemctl restart nginx
```

Enable service:

```bash
sudo systemctl enable nginx
```

Disable service:

```bash
sudo systemctl disable nginx
```

List services:

```bash
systemctl list-units --type=service
```

---

# Process Management

```bash
ps aux
top
htop
kill PID
killall process
pgrep process
jobs
bg
fg
```

---

# Storage Management

Disk usage:

```bash
df -h
```

Directory size:

```bash
du -sh folder
```

Block devices:

```bash
lsblk
```

Filesystem information:

```bash
blkid
```

Mount filesystems:

```bash
mount
```

Unmount:

```bash
umount
```

---

# File Permissions

View permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod 755 file
```

Change owner:

```bash
chown user file
```

Change group:

```bash
chgrp developers file
```

---

# Networking

View IP address:

```bash
ip addr
```

Display routes:

```bash
ip route
```

Test connectivity:

```bash
ping google.com
```

Download files:

```bash
wget URL
curl URL
```

SSH connection:

```bash
ssh user@host
```

Listening ports:

```bash
ss -tuln
```

---

# Log Management

System logs:

```bash
journalctl
```

Follow logs:

```bash
journalctl -f
```

Kernel logs:

```bash
dmesg
```

Authentication logs:

```bash
sudo tail -f /var/log/auth.log
```

---

# Scheduling Tasks

Edit cron jobs:

```bash
crontab -e
```

List cron jobs:

```bash
crontab -l
```

One-time task:

```bash
at 15:00
```

---

# System Monitoring

Memory usage:

```bash
free -h
```

CPU information:

```bash
lscpu
```

Disk I/O:

```bash
iostat
```

Virtual memory:

```bash
vmstat
```

Open files:

```bash
lsof
```

---

# Security

Firewall status:

```bash
sudo ufw status
```

Enable firewall:

```bash
sudo ufw enable
```

Allow SSH:

```bash
sudo ufw allow 22
```

Check failed logins:

```bash
lastb
```

View sudo permissions:

```bash
sudo visudo
```

---

# Compression

```bash
tar -cvf archive.tar folder
tar -xvf archive.tar
zip archive.zip folder
unzip archive.zip
gzip file
gunzip file.gz
```

---

# Backup

Create archive:

```bash
tar -czvf backup.tar.gz folder/
```

Synchronize files:

```bash
rsync -av source/ destination/
```

Copy directory:

```bash
cp -r source backup
```

---

# Environment Variables

Display variables:

```bash
env
```

Display PATH:

```bash
echo $PATH
```

Create variable:

```bash
export VAR=value
```

Remove variable:

```bash
unset VAR
```

---

# Common Maintenance Tasks

Update packages:

```bash
sudo apt update && sudo apt upgrade
```

Remove unused packages:

```bash
sudo apt autoremove
```

Check filesystem:

```bash
sudo fsck /dev/sda1
```

Clean package cache:

```bash
sudo apt clean
```

---

# Useful Commands

```bash
uname
hostnamectl
systemctl
journalctl
ps
top
free
df
du
lsblk
mount
umount
chmod
chown
useradd
usermod
passwd
ip
ping
ssh
rsync
tar
crontab
history
```

---

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Stop current command |
| `Ctrl + D` | Exit terminal |
| `Ctrl + L` | Clear terminal |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete |

---

# Best Practices

- Keep the operating system updated.
- Regularly monitor system logs.
- Use strong passwords and SSH keys.
- Follow the Principle of Least Privilege.
- Back up important data frequently.
- Monitor disk space and system resources.
- Remove unused packages and user accounts.
- Review running services periodically.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Ignoring updates | Apply security updates regularly |
| Running everything as root | Use `sudo` when needed |
| Forgetting backups | Schedule automated backups |
| Ignoring logs | Monitor logs regularly |
| Using weak passwords | Enforce strong password policies |
| Leaving unused services enabled | Disable unnecessary services |

---

# Quick Reference

```bash
systemctl status service
journalctl -f
ps aux
top
free -h
df -h
du -sh folder
lsblk
chmod 755 file
chown user file
useradd username
passwd username
apt update
apt upgrade
ip addr
ping google.com
crontab -e
rsync -av source destination
```

---

# Related Topics

- System Administration
- User Management
- Process Management
- Package Management
- Networking
- Security
- Storage Management
- Linux Commands
```