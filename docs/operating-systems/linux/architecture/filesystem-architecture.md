# Filesystem Architecture

## Overview

The Linux filesystem architecture defines how files, directories, storage devices, and mounted filesystems are organized within the operating system.

Unlike Windows, which uses separate drive letters (C:, D:, etc.), Linux organizes everything into a **single hierarchical directory tree** that starts from the **root directory (`/`)**.

This unified structure allows Linux to manage files, devices, and storage consistently.

---

## Filesystem Hierarchy

```text
                /
                │
 ├──────────────┼───────────────────────────┐
 │              │                           │
bin           boot                       dev
etc           home                       lib
media         mnt                        opt
proc          root                       run
sbin          srv                        sys
tmp           usr                        var
```

Every file and directory on a Linux system exists somewhere under the root (`/`).

---

## Root Directory (/)

The **root directory** is the highest level of the Linux filesystem.

It contains every directory, file, and mounted storage device.

Example:

```text
/
├── bin
├── etc
├── home
├── usr
└── var
```

---

## Important Directories

### `/bin`

Contains essential user commands required during system startup and recovery.

Examples:

- ls
- cp
- mv
- rm
- cat

Example:

```bash
ls /bin
```

---

### `/boot`

Stores files required during system boot.

Contains:

- Linux kernel
- GRUB bootloader files
- initramfs

Example:

```text
/boot
├── vmlinuz
├── initrd.img
└── grub/
```

---

### `/dev`

Contains device files representing hardware devices.

Examples:

```text
/dev/sda
/dev/null
/dev/random
/dev/tty
```

Everything in Linux is treated as a file—even hardware devices.

---

### `/etc`

Contains system-wide configuration files.

Examples:

```text
/etc/passwd
/etc/hostname
/etc/fstab
/etc/ssh/
```

Avoid storing user files here.

---

### `/home`

Contains personal directories for normal users.

Example:

```text
/home
├── alice
├── bob
└── john
```

A user's documents, downloads, and configuration files are typically stored here.

---

### `/root`

Home directory of the root (administrator) user.

Do not confuse this with the root directory (`/`).

---

### `/lib`

Contains shared libraries required by essential system programs.

Examples:

```text
/lib
/lib64
```

---

### `/media`

Temporary mount point for removable storage devices.

Examples:

- USB drives
- DVDs
- SD cards

---

### `/mnt`

Used for manually mounting filesystems.

Example:

```bash
sudo mount /dev/sdb1 /mnt
```

---

### `/opt`

Contains optional third-party software.

Examples:

```text
/opt/google
/opt/vscode
```

---

### `/proc`

A virtual filesystem that provides information about running processes and the kernel.

Examples:

```text
/proc/cpuinfo
/proc/meminfo
/proc/version
```

Example:

```bash
cat /proc/cpuinfo
```

---

### `/run`

Stores temporary runtime information created after system startup.

Examples:

- PID files
- Runtime sockets

Contents are cleared after reboot.

---

### `/sbin`

Contains essential system administration commands.

Examples:

- fsck
- reboot
- shutdown
- mount

Usually intended for administrative users.

---

### `/srv`

Stores data served by system services.

Examples:

- Web server files
- FTP server data

---

### `/sys`

Virtual filesystem exposing kernel and hardware information.

Useful for inspecting devices and kernel settings.

---

### `/tmp`

Stores temporary files.

Characteristics:

- Readable and writable by all users
- Automatically cleaned on reboot (depending on configuration)

Example:

```bash
touch /tmp/example.txt
```

---

### `/usr`

Contains user applications, libraries, and documentation.

Subdirectories include:

```text
/usr/bin
/usr/lib
/usr/share
/usr/local
```

Most installed software resides here.

---

### `/var`

Stores files that change frequently.

Examples:

- Logs
- Mail
- Cache
- Databases
- Print queues

Important directory:

```text
/var/log
```

---

## Mounted Filesystems

Linux allows multiple storage devices to appear as part of the same directory tree.

Example:

```text
/
├── home
├── boot
└── media
      └── USB
```

The USB drive is mounted under `/media` but becomes part of the same filesystem hierarchy.

View mounted filesystems:

```bash
mount
```

or

```bash
findmnt
```

---

## Filesystem Types

Common Linux filesystem types include:

| Filesystem | Description |
|------------|-------------|
| ext4 | Default filesystem for many Linux distributions |
| XFS | High-performance journaling filesystem |
| Btrfs | Modern filesystem with snapshots and compression |
| FAT32 | Compatible with Windows and USB drives |
| NTFS | Windows filesystem with Linux support |
| exFAT | Common for flash drives and SD cards |

---

## Virtual Filesystems

Some directories do not exist physically on disk.

Examples:

- `/proc`
- `/sys`
- `/dev`

These are created dynamically by the kernel to provide access to system and hardware information.

---

## Filesystem Hierarchy Standard (FHS)

Most Linux distributions follow the **Filesystem Hierarchy Standard (FHS)**.

FHS defines:

- Directory names
- Directory purposes
- Standard filesystem organization

This consistency makes Linux systems easier to administer across distributions.

---

## Common Commands

Display filesystem usage:

```bash
df -h
```

Display directory sizes:

```bash
du -sh *
```

View mounted filesystems:

```bash
findmnt
```

List root directories:

```bash
ls /
```

Show filesystem type:

```bash
df -T
```

Display block devices:

```bash
lsblk
```

---

## Best Practices

- Do not modify system directories unless necessary.
- Store personal files inside `/home`.
- Keep configuration files in `/etc`.
- Use `/tmp` only for temporary data.
- Monitor `/var/log` for troubleshooting.
- Mount external storage under `/media` or `/mnt`.

---

## Key Takeaways

- Linux organizes everything under a single root directory (`/`).
- Files, devices, and mounted storage share the same directory hierarchy.
- Each top-level directory has a specific purpose defined by the Filesystem Hierarchy Standard (FHS).
- Virtual filesystems such as `/proc` and `/sys` provide real-time system information.
- Understanding the filesystem architecture is essential for system administration and troubleshooting.

---

## Related Topics

- Linux Architecture
- Files and Directories
- Filesystem Hierarchy
- Package Management
- Boot Sequence