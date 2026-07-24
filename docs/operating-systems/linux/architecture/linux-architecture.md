# Linux Architecture

## Overview

Linux architecture is the layered design of the Linux operating system. It defines how hardware, the kernel, system libraries, system utilities, and user applications interact with each other.

This layered architecture improves **security**, **stability**, **portability**, and **maintainability** by separating responsibilities across different components.

---

## Linux Architecture Diagram

```text
+------------------------------------------------------+
|                  User Applications                   |
|------------------------------------------------------|
| Browser | Terminal | VS Code | Python | Database     |
+------------------------------------------------------+
                       │
                       ▼
+------------------------------------------------------+
|                 System Libraries                     |
|------------------------------------------------------|
| glibc | OpenSSL | GTK | Qt | POSIX Libraries         |
+------------------------------------------------------+
                       │
                       ▼
+------------------------------------------------------+
|                  System Calls                        |
+------------------------------------------------------+
                       │
                       ▼
+------------------------------------------------------+
|                   Linux Kernel                       |
|------------------------------------------------------|
| Process Management                                   |
| Memory Management                                    |
| File Systems                                         |
| Device Drivers                                       |
| Networking                                           |
| Security                                             |
| IPC                                                  |
+------------------------------------------------------+
                       │
                       ▼
+------------------------------------------------------+
|                     Hardware                         |
|------------------------------------------------------|
| CPU | RAM | Disk | GPU | Keyboard | Network | USB    |
+------------------------------------------------------+
```

---

# Architecture Layers

Linux is commonly divided into five layers:

1. Hardware
2. Kernel
3. System Libraries
4. System Utilities
5. User Applications

---

# 1. Hardware Layer

The hardware layer consists of all physical components of the computer.

Examples include:

- CPU
- RAM
- Hard Disk / SSD
- Network Interface Card (NIC)
- Keyboard
- Mouse
- GPU
- USB Devices

Applications never communicate directly with hardware. Instead, all communication passes through the Linux kernel.

---

# 2. Linux Kernel

The kernel is the core of the Linux operating system.

It acts as an intermediary between hardware and user applications.

Its responsibilities include:

- Process management
- Memory management
- Device driver management
- File system management
- Network management
- Security and permissions
- Interrupt handling

The kernel runs in **Kernel Space**, where it has full access to system resources.

---

## Kernel Components

### Process Management

Responsible for:

- Creating processes
- Scheduling CPU time
- Process synchronization
- Process termination

Example command:

```bash
ps
```

---

### Memory Management

Responsible for:

- RAM allocation
- Virtual memory
- Paging
- Swapping
- Memory protection

Example command:

```bash
free -h
```

---

### Device Drivers

Device drivers allow Linux to communicate with hardware devices.

Examples:

- Keyboard driver
- Printer driver
- Network driver
- Graphics driver

Without drivers, hardware cannot function correctly.

---

### File System Management

Responsible for:

- Creating files
- Reading and writing files
- Managing permissions
- Mounting storage devices

Supported filesystems include:

- ext4
- XFS
- Btrfs
- FAT32
- NTFS

---

### Networking

The kernel manages:

- TCP/IP
- UDP
- Routing
- Firewalls
- Network interfaces
- Socket communication

Example:

```bash
ip addr
```

---

# 3. System Libraries

System libraries provide standard functions that applications use to interact with the kernel.

Instead of communicating directly with the kernel, applications call library functions, which internally invoke system calls.

Common libraries include:

- glibc
- OpenSSL
- GTK
- Qt
- POSIX libraries

Example:

```c
printf("Hello World");
```

Internally, the library interacts with the kernel when required.

---

# 4. System Utilities

System utilities are programs that help users manage and administer the operating system.

Examples include:

- Bash
- ls
- cp
- mv
- grep
- systemctl
- journalctl
- ssh
- tar

These utilities simplify interaction with the operating system.

---

# 5. User Applications

User applications run in **User Space**.

Examples include:

- Firefox
- Google Chrome
- Visual Studio Code
- LibreOffice
- VLC
- Docker
- Git
- Python programs

Applications cannot directly access hardware.

Instead, they communicate with the kernel through system calls.

---

# User Space vs Kernel Space

Linux separates execution into two protected memory regions.

| User Space | Kernel Space |
|------------|--------------|
| Applications | Linux Kernel |
| Limited privileges | Full hardware access |
| Cannot directly access hardware | Controls all hardware |
| Runs in Ring 3 | Runs in Ring 0 |

This separation improves system security and stability.

---

# System Call Flow

Whenever an application needs a system resource, it uses a system call.

```text
Application
      │
      ▼
System Library
      │
      ▼
System Call
      │
      ▼
Linux Kernel
      │
      ▼
Hardware
```

Example:

Opening a file:

```text
Application
      │
open()
      │
System Call
      │
Kernel
      │
Disk
```

---

# Boot Process Within the Architecture

Linux startup follows this sequence:

```text
Power On
    │
    ▼
BIOS / UEFI
    │
    ▼
GRUB Bootloader
    │
    ▼
Linux Kernel
    │
    ▼
Initramfs
    │
    ▼
systemd
    │
    ▼
System Services
    │
    ▼
User Login
```

---

# Why Linux Uses a Layered Architecture

The layered design offers several benefits:

- Improved security through isolation
- Better system stability
- Easier hardware support via drivers
- Modular design for easier maintenance
- High portability across different hardware platforms

---

# Common Commands

Display kernel version:

```bash
uname -r
```

Display architecture information:

```bash
uname -m
```

View CPU information:

```bash
lscpu
```

Display block devices:

```bash
lsblk
```

View loaded kernel modules:

```bash
lsmod
```

Display kernel messages:

```bash
dmesg
```

---

# Best Practices

- Keep the Linux kernel updated.
- Install only trusted software and drivers.
- Avoid running applications with unnecessary root privileges.
- Regularly monitor system logs and hardware health.
- Understand the role of each architecture layer before troubleshooting.

---

# Key Takeaways

- Linux follows a layered architecture consisting of Hardware, Kernel, System Libraries, System Utilities, and User Applications.
- The kernel is the core of the operating system and manages hardware and system resources.
- Applications interact with the kernel using system calls.
- Kernel Space and User Space are separated to improve security and stability.
- The modular design of Linux makes it portable, reliable, and easy to maintain.

---

## Related Topics

- Boot Sequence
- Filesystem Architecture
- Kernel Space vs User Space
- Memory Management
- Process Lifecycle
- System Startup
- System Calls