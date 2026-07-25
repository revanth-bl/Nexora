# Filesystem Cheat Sheet

## Overview

The Linux filesystem organizes data in a hierarchical directory structure rooted at `/`. Everything in Linux—including files, directories, devices, and processes—is represented as a file. This cheat sheet provides a quick reference to filesystem navigation, directory structure, permissions, mounting, disk usage, and essential filesystem commands.

---

# Filesystem Hierarchy

| Directory | Purpose |
|-----------|---------|
| `/` | Root directory |
| `/bin` | Essential user binaries |
| `/sbin` | System administration binaries |
| `/boot` | Bootloader and kernel files |
| `/dev` | Device files |
| `/etc` | System configuration files |
| `/home` | User home directories |
| `/lib` | Shared libraries |
| `/media` | Removable media |
| `/mnt` | Temporary mount point |
| `/opt` | Optional software |
| `/proc` | Process information |
| `/root` | Root user's home directory |
| `/run` | Runtime data |
| `/srv` | Service data |
| `/sys` | Kernel information |
| `/tmp` | Temporary files |
| `/usr` | User applications and utilities |
| `/var` | Variable data (logs, cache, mail) |

---

# Navigation Commands

```bash
pwd
ls
ls -l
ls -la
cd
cd ..
cd ~
tree
```

---

# File Operations

```bash
touch file.txt
mkdir folder
mkdir -p dir/subdir
cp source destination
cp -r folder backup
mv old.txt new.txt
rm file.txt
rm -r folder
```

---

# Viewing Files

```bash
cat file.txt
less file.txt
head file.txt
tail file.txt
tail -f logfile.log
```

---

# Searching Files

```bash
find . -name "*.txt"
find / -type f
find . -size +100M
locate filename
```

---

# Disk Usage

```bash
df -h
du -sh folder
du -ah
lsblk
```

---

# Mounting Filesystems

List mounted filesystems:

```bash
mount
```

Mount a device:

```bash
sudo mount /dev/sdb1 /mnt
```

Unmount:

```bash
sudo umount /mnt
```

View filesystem table:

```bash
cat /etc/fstab
```

---

# Filesystem Types

| Filesystem | Description |
|------------|-------------|
| ext4 | Default Linux filesystem |
| XFS | High-performance filesystem |
| Btrfs | Modern copy-on-write filesystem |
| FAT32 | Cross-platform compatibility |
| exFAT | Large removable drives |
| NTFS | Windows filesystem |
| tmpfs | RAM-based temporary filesystem |
| ISO9660 | CD/DVD filesystem |

---

# Permissions

View permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod 755 file
chmod +x script.sh
```

Change ownership:

```bash
chown user file
chgrp developers file
```

---

# Symbolic and Hard Links

Create a symbolic link:

```bash
ln -s target shortcut
```

Create a hard link:

```bash
ln source link
```

---

# File Compression

```bash
tar -cvf archive.tar folder
tar -xvf archive.tar
zip archive.zip folder
unzip archive.zip
gzip file
gunzip file.gz
```

---

# File Information

```bash
stat file.txt
file file.txt
wc file.txt
```

---

# Filesystem Checking

Check filesystem:

```bash
sudo fsck /dev/sda1
```

Check disk usage:

```bash
df -h
```

Repair filesystem:

```bash
sudo fsck -y /dev/sda1
```

---

# Useful Wildcards

| Pattern | Matches |
|---------|---------|
| `*` | Any characters |
| `?` | Single character |
| `[abc]` | One listed character |
| `[0-9]` | Any digit |

Examples:

```bash
ls *.txt
rm file?.log
```

---

# Redirection

```bash
command > output.txt
command >> output.txt
command < input.txt
command 2> error.log
command > output.log 2>&1
```

---

# Common File Attributes

Display attributes:

```bash
lsattr file
```

Change attributes:

```bash
chattr +i file
```

Remove immutable flag:

```bash
chattr -i file
```

---

# Filesystem Utilities

```bash
sync
mount
umount
fsck
mkfs.ext4
blkid
df
du
```

---

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Tab` | Auto-complete |
| `Ctrl + C` | Stop command |
| `Ctrl + D` | Exit terminal |
| `Ctrl + L` | Clear screen |
| `Ctrl + R` | Search history |

---

# Common Tasks

Create nested directories:

```bash
mkdir -p projects/linux/docs
```

Copy a directory:

```bash
cp -r source backup
```

Delete a directory:

```bash
rm -r folder
```

Find large files:

```bash
find / -type f -size +500M
```

Show disk usage:

```bash
du -sh *
```

Display free disk space:

```bash
df -h
```

---

# Best Practices

- Organize files using meaningful directory names.
- Avoid storing data directly under the root (`/`) directory.
- Use symbolic links when appropriate.
- Regularly monitor disk usage.
- Keep backups of important files.
- Apply the principle of least privilege to file permissions.
- Clean temporary files periodically.
- Verify mounted filesystems before performing maintenance.

---

# Related Topics

- Filesystem Hierarchy
- File Management
- Permissions
- Disk Storage
- Linux Commands
- Mounting Filesystems
- System Administration
- Storage Management