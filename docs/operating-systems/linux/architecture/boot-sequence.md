# Boot Sequence

## Overview

The Linux boot sequence is the series of steps that occur from the moment a computer is powered on until the user is presented with a login prompt or graphical desktop.

Understanding the boot process is essential for troubleshooting startup issues, configuring bootloaders, and managing Linux systems.

---

## Boot Sequence Flow

```text
Power On
    │
    ▼
BIOS / UEFI
    │
    ▼
Bootloader (GRUB)
    │
    ▼
Linux Kernel
    │
    ▼
Initramfs (Initial RAM Filesystem)
    │
    ▼
systemd (or init)
    │
    ▼
System Services
    │
    ▼
Login Screen / Shell
```

---

## Step 1: Power On

When the computer is powered on:

- CPU resets itself.
- Firmware starts executing.
- Hardware initialization begins.

This marks the beginning of the boot process.

---

## Step 2: BIOS or UEFI

The firmware performs a **POST (Power-On Self-Test)** to verify that hardware components such as:

- CPU
- RAM
- Keyboard
- Storage devices

are functioning correctly.

After POST, the firmware searches for a bootable device.

### BIOS

Older firmware that uses the **MBR (Master Boot Record)**.

### UEFI

Modern firmware that uses the **EFI System Partition (ESP)** and offers:

- Faster boot times
- Secure Boot
- GPT support
- Larger disk support

---

## Step 3: Bootloader (GRUB)

The bootloader loads the Linux operating system.

The most common Linux bootloader is **GRUB (Grand Unified Bootloader)**.

Responsibilities include:

- Displaying the boot menu
- Loading the Linux kernel
- Loading initramfs
- Passing kernel parameters

Example:

```text
GRUB
 ↓
Linux Kernel
 ↓
initramfs
```

---

## Step 4: Linux Kernel

The kernel is loaded into memory and takes control of the system.

During initialization it:

- Detects hardware
- Initializes device drivers
- Mounts the temporary root filesystem
- Starts the first userspace process

---

## Step 5: Initramfs

**Initramfs (Initial RAM Filesystem)** is a temporary root filesystem loaded into memory.

Its purpose is to:

- Load required kernel modules
- Detect storage devices
- Mount the real root filesystem
- Hand control to the actual operating system

Without initramfs, many modern Linux systems would be unable to locate the root filesystem.

---

## Step 6: Init System

Once the real root filesystem is mounted, the kernel starts the init system.

Modern Linux distributions use **systemd**.

Older systems may use:

- SysVinit
- Upstart

The init system is responsible for:

- Starting services
- Mounting filesystems
- Configuring networking
- Managing user sessions

---

## Step 7: System Services

systemd starts essential services such as:

- Network Manager
- SSH Server
- Logging services
- Display Manager
- Cron scheduler

Services may start in parallel, making boot significantly faster.

---

## Step 8: Login

Finally, Linux presents either:

- Graphical login manager
- Terminal login prompt

After authentication, the user gains access to the system.

---

# Complete Boot Flow

```text
Power Button
      │
      ▼
 BIOS / UEFI
      │
      ▼
 POST
      │
      ▼
 Boot Device
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
 Root Filesystem
      │
      ▼
 systemd
      │
      ▼
 Services
      │
      ▼
 Login Screen
```

---

# Common Boot Problems

| Problem | Possible Cause |
|----------|----------------|
| GRUB missing | Bootloader corruption |
| Kernel panic | Missing root filesystem or driver |
| Black screen | Graphics driver issue |
| Stuck at boot | Failed system service |
| Boot loop | Incorrect kernel or boot configuration |

---

# Useful Commands

View boot logs:

```bash
journalctl -b
```

View previous boot logs:

```bash
journalctl -b -1
```

Show current kernel:

```bash
uname -r
```

View bootloader configuration:

```bash
cat /boot/grub/grub.cfg
```

Check systemd boot performance:

```bash
systemd-analyze
```

Detailed boot timing:

```bash
systemd-analyze blame
```

---

# Key Takeaways

- The Linux boot process follows a predictable sequence from firmware to user login.
- BIOS/UEFI initializes hardware before loading the bootloader.
- GRUB loads the Linux kernel and initramfs.
- The kernel initializes hardware and starts the init system.
- systemd launches services and prepares the operating system for user interaction.

---

## Related Topics

- Linux Architecture
- Kernel Space vs User Space
- System Startup
- Process Lifecycle
- Memory Management