# System Startup

## Overview

System startup is the phase that begins after the Linux kernel has successfully booted and mounted the root filesystem. During this stage, the **init system** initializes the operating system by starting essential services, mounting filesystems, configuring networking, and preparing the system for user interaction.

Most modern Linux distributions use **systemd** as the default init system.

---

# System Startup Flow

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
Initramfs
     │
     ▼
Root Filesystem Mounted
     │
     ▼
systemd (PID 1)
     │
     ├── Mount Filesystems
     ├── Start Services
     ├── Configure Networking
     ├── Initialize Logging
     ├── Start Display Manager
     │
     ▼
Login Screen / Terminal
```

---

# What is System Startup?

System startup refers to everything that happens **after the kernel has taken control of the system**.

Its primary goals are:

- Prepare the operating system
- Start required system services
- Configure hardware and networking
- Allow users to log in

Without the startup process, Linux would boot the kernel but remain unusable.

---

# Init System

The **init system** is the first userspace process started by the Linux kernel.

It always has:

```text
PID 1
```

Modern Linux distributions use:

- systemd

Older init systems include:

- SysVinit
- Upstart

---

# systemd

**systemd** is the default initialization and service manager on most Linux distributions.

Responsibilities include:

- Starting system services
- Managing daemons
- Mounting filesystems
- Configuring networking
- Handling user sessions
- Managing system shutdown and reboot
- Collecting logs through journald

Example:

```bash
ps -p 1
```

Output:

```text
PID TTY          TIME CMD
1 ?        00:00:02 systemd
```

---

# Startup Targets

systemd groups services into **targets**, which represent different system states.

Common targets include:

| Target | Purpose |
|---------|---------|
| `multi-user.target` | Multi-user text mode |
| `graphical.target` | Graphical desktop environment |
| `rescue.target` | Single-user rescue mode |
| `emergency.target` | Minimal emergency shell |

Display the current target:

```bash
systemctl get-default
```

---

# Starting System Services

During startup, systemd launches essential services such as:

- Network Manager
- SSH Server
- Logging Service
- Time Synchronization
- Display Manager
- Cron Scheduler
- Firewall

Unlike older init systems, systemd can start many services **in parallel**, reducing boot time.

---

# Mounting Filesystems

Before users can access files, Linux mounts required filesystems.

Examples include:

- Root filesystem (`/`)
- `/boot`
- `/home`
- `/tmp`
- External storage

Configuration is stored in:

```text
/etc/fstab
```

Display mounted filesystems:

```bash
findmnt
```

---

# Networking Initialization

Networking services configure:

- Network interfaces
- IP addresses
- DNS
- Routing

Example services:

- NetworkManager
- systemd-networkd

Check network status:

```bash
ip addr
```

---

# Logging Initialization

systemd starts the **journald** service to collect system logs.

Logs include:

- Kernel messages
- Boot logs
- Service logs
- Security events

View logs:

```bash
journalctl
```

Boot logs:

```bash
journalctl -b
```

---

# Display Manager

On systems with a graphical interface, systemd starts a **Display Manager**.

Common display managers include:

- GDM
- SDDM
- LightDM

The display manager presents the graphical login screen after startup.

---

# User Login

After startup completes, Linux provides either:

- Graphical login screen
- Terminal login prompt

After successful authentication:

- User shell starts
- User environment is loaded
- Desktop session begins (if applicable)

---

# Service Startup Process

```text
systemd
   │
   ├── Networking
   ├── Logging
   ├── SSH
   ├── Cron
   ├── Firewall
   ├── Display Manager
   └── Other Services
```

---

# Startup Performance

systemd provides tools to analyze boot performance.

Show total startup time:

```bash
systemd-analyze
```

Show startup timing:

```bash
systemd-analyze blame
```

Show dependency tree:

```bash
systemd-analyze critical-chain
```

These commands help identify slow services during boot.

---

# Common Commands

Check system status:

```bash
systemctl status
```

View running services:

```bash
systemctl list-units --type=service
```

Start a service:

```bash
sudo systemctl start <service>
```

Stop a service:

```bash
sudo systemctl stop <service>
```

Restart a service:

```bash
sudo systemctl restart <service>
```

Enable a service at boot:

```bash
sudo systemctl enable <service>
```

Disable a service:

```bash
sudo systemctl disable <service>
```

View boot logs:

```bash
journalctl -b
```

Analyze boot performance:

```bash
systemd-analyze
```

---

# Best Practices

- Enable only necessary services at startup.
- Monitor boot performance regularly.
- Review startup logs for errors.
- Keep system services updated.
- Disable unused services to reduce boot time and improve security.
- Use `systemctl` instead of legacy service management commands whenever possible.

---

# Common Startup Problems

| Problem | Possible Cause |
|----------|----------------|
| Slow boot | Too many startup services |
| Failed login screen | Display manager failure |
| Network unavailable | Networking service not started |
| Service failed to start | Configuration error or missing dependency |
| Boot hangs | Filesystem or hardware issue |

---

# Key Takeaways

- System startup begins after the Linux kernel has initialized the hardware and mounted the root filesystem.
- **systemd (PID 1)** is the default init system on most modern Linux distributions.
- During startup, Linux mounts filesystems, starts services, configures networking, initializes logging, and prepares the system for user login.
- systemd starts services in parallel, improving boot performance.
- Commands such as `systemctl`, `journalctl`, and `systemd-analyze` are essential for managing and troubleshooting the startup process.

---

## Related Topics

- Linux Architecture
- Boot Sequence
- Kernel Space vs User Space
- Process Lifecycle
- Memory Management
- Filesystem Architecture
- System Services
```