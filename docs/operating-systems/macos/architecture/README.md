# macOS Architecture

## Overview

This section explains how macOS is structured internally, from the kernel and system startup process to memory, networking, processes, and background services.

The goal is to understand **how the major components of macOS work together**, rather than simply memorizing commands.

---

## Architecture at a Glance

A simplified macOS architecture looks like this:

```text
┌──────────────────────────────────────┐
│            Applications              │
│     GUI Apps • CLI Tools • Services  │
└──────────────────┬───────────────────┘
                   │
┌──────────────────▼───────────────────┐
│        macOS Frameworks / APIs       │
│ Foundation • AppKit • Network        │
│ Security • I/O • Other Frameworks    │
└──────────────────┬───────────────────┘
                   │
┌──────────────────▼───────────────────┐
│             Darwin                    │
│ BSD • POSIX • User-Space Services    │
└──────────────────┬───────────────────┘
                   │
┌──────────────────▼───────────────────┐
│               XNU                     │
│ Mach • BSD • I/O Kit                 │
└──────────────────┬───────────────────┘
                   │
┌──────────────────▼───────────────────┐
│             Hardware                  │
│ CPU • Memory • Storage • Network     │
└──────────────────────────────────────┘
```

---

# What This Section Covers

The architecture section focuses on the major mechanisms that make macOS operate.

### Core Topics

- System startup
- Boot process
- XNU kernel
- Kernel space and user space
- Memory management
- Process lifecycle
- Networking architecture
- Filesystem architecture
- `launchd` and services

---

# Architecture Files

| File | Description |
|---|---|
| `boot-process.md` | How a Mac progresses from power-on to a running operating system |
| `filesystem-architecture.md` | Structure and organization of the macOS filesystem |
| `kernel-and-xnu.md` | XNU, Mach, BSD, and the macOS kernel architecture |
| `kernel-space-vs-users.md` | Differences between kernel space and user space |
| `launchd-and-services.md` | `launchd`, daemons, agents, and service management |
| `linux-achitecture.md` | Linux architecture for comparison with macOS |
| `memory-management.md` | Virtual memory, physical memory, compression, and swap |
| `networking-architecture.md` | macOS networking stack, interfaces, routing, and protocols |
| `process-lifecycle.md` | Process creation, execution, scheduling, and termination |
| `system-startup.md` | macOS startup sequence and system initialization |

---

# macOS Architectural Layers

## 1. Hardware

At the lowest level are the physical components:

```text
CPU
RAM
Storage
GPU
Network Hardware
Input / Output Devices
```

The operating system communicates with this hardware through kernel components and drivers.

---

## 2. XNU Kernel

XNU is the kernel at the core of macOS.

It combines technologies including:

```text
XNU
│
├── Mach
├── BSD
└── I/O Kit
```

The kernel manages fundamental resources such as:

- Processes
- Threads
- Memory
- Networking
- Hardware access
- Filesystems
- Security boundaries

---

## 3. Darwin

Darwin forms the open-source Unix foundation underneath macOS.

It includes major components such as:

- XNU
- BSD userland components
- POSIX interfaces
- Core system utilities

macOS adds Apple's proprietary frameworks and technologies on top of this foundation.

---

## 4. System Frameworks

Applications generally interact with macOS through APIs and frameworks rather than directly accessing kernel internals.

Examples include:

```text
Foundation
AppKit
Network.framework
Security.framework
Core Foundation
```

These frameworks provide higher-level functionality to applications.

---

## 5. Applications

At the highest level are user applications.

Examples include:

```text
Terminal
Safari
Finder
Editors
Development Tools
Third-Party Applications
```

Applications ultimately depend on the lower layers of the operating system.

---

# Kernel Space and User Space

macOS separates privileged kernel execution from normal application execution.

```text
User Space
────────────────────────
Applications
System Services
Utilities
────────────────────────
Kernel Boundary
────────────────────────
Kernel Space
────────────────────────
XNU
Drivers
Kernel Subsystems
────────────────────────
Hardware
```

This separation provides important security and stability boundaries.

---

# System Startup

The startup process can be simplified as:

```text
Power On
   │
   ▼
Firmware / Boot Environment
   │
   ▼
Boot Components
   │
   ▼
XNU Kernel
   │
   ▼
launchd
   │
   ▼
System Services
   │
   ▼
User Environment
```

The exact boot sequence differs between Intel-based Macs and Apple silicon Macs.

---

# Process Architecture

Processes provide the execution environment for applications and services.

```text
launchd
   │
   ├── System Daemon
   │
   ├── Service
   │
   └── Application
          │
          ├── Thread
          ├── Thread
          └── Thread
```

The XNU kernel schedules these threads and manages their resources.

---

# Memory Architecture

macOS provides each process with a virtual address space.

```text
Process
   │
   ▼
Virtual Memory
   │
   ▼
XNU Memory Management
   │
   ├── Physical RAM
   ├── Compressed Memory
   ├── File Cache
   └── Swap
```

Apple silicon systems additionally use a unified memory architecture where CPU and GPU resources share the same memory system.

---

# Networking Architecture

Network communication follows a layered design:

```text
Application
     │
     ▼
Network APIs
     │
     ▼
BSD Sockets / Network.framework
     │
     ▼
TCP / UDP
     │
     ▼
IP
     │
     ▼
Network Interface
     │
     ▼
Hardware
```

This architecture allows applications to communicate over Wi-Fi, Ethernet, VPNs, and other network technologies without directly managing hardware.

---

# Filesystem Architecture

The filesystem provides persistent storage to applications and system components.

A simplified view is:

```text
Application
     │
     ▼
Filesystem APIs
     │
     ▼
VFS
     │
     ▼
Filesystem
     │
     ▼
Storage
```

Modern macOS commonly uses **APFS** for its primary filesystem.

---

# launchd and Services

`launchd` is a central service-management component in macOS.

The system instance runs as:

```text
PID 1
```

It manages many:

- Daemons
- Agents
- Background services
- Scheduled jobs
- On-demand services

The command-line interface is:

```bash
launchctl
```

---

# Security Architecture

Security is integrated throughout the operating system.

Important mechanisms include:

```text
Application
     │
     ├── Sandbox
     ├── Code Signing
     ├── Entitlements
     └── Privacy Controls
            │
            ▼
       System Security
            │
            ▼
           XNU
```

Other important technologies include:

- System Integrity Protection
- Secure Boot
- Gatekeeper
- FileVault
- Address Space Layout Randomization
- Hardware-backed security features

---

# Intel vs Apple Silicon

macOS runs on different hardware architectures.

### Intel Macs

```text
Intel x86-64
     │
     ▼
macOS
     │
     ▼
XNU
```

### Apple Silicon Macs

```text
ARM-based Apple Silicon
     │
     ▼
macOS
     │
     ▼
XNU
```

Many operating-system concepts remain consistent, but boot architecture, memory architecture, hardware interfaces, and virtualization behavior can differ significantly.

---

# Recommended Learning Order

For understanding macOS architecture, study the topics in this order:

```text
1. System Startup
       │
       ▼
2. Boot Process
       │
       ▼
3. Kernel and XNU
       │
       ▼
4. Kernel Space vs User Space
       │
       ▼
5. Process Lifecycle
       │
       ▼
6. Memory Management
       │
       ▼
7. Filesystem Architecture
       │
       ▼
8. Networking Architecture
       │
       ▼
9. launchd and Services
```

This order moves from system initialization toward the individual subsystems that operate after startup.

---

# Architecture Troubleshooting Mindset

When troubleshooting macOS, think in layers.

```text
Application
    │
    ▼
Framework / API
    │
    ▼
User-Space Service
    │
    ▼
Kernel
    │
    ▼
Driver
    │
    ▼
Hardware
```

If something fails, determine **which layer is responsible** before attempting random fixes.

For example:

```text
Network Problem
      │
      ├── Application?
      ├── DNS?
      ├── Routing?
      ├── Network Interface?
      ├── Driver?
      └── Hardware?
```

This approach is far more reliable than repeatedly restarting the machine and hoping for divine intervention.

---

# Key Concepts

The most important concepts in this section are:

- XNU
- Mach
- BSD
- Darwin
- Kernel space
- User space
- Processes
- Threads
- Virtual memory
- Memory compression
- APFS
- TCP/IP
- Network interfaces
- `launchd`
- Daemons
- Agents
- System startup
- Boot process

---

# Summary

macOS is a layered operating system built around the XNU kernel and Darwin foundation.

The overall architecture can be summarized as:

```text
┌─────────────────────────────┐
│        Applications         │
├─────────────────────────────┤
│     macOS Frameworks        │
├─────────────────────────────┤
│          Darwin             │
├─────────────────────────────┤
│            XNU              │
│     Mach + BSD + I/O Kit    │
├─────────────────────────────┤
│          Hardware           │
└─────────────────────────────┘
```

The purpose of this section is to understand how these layers interact and how macOS transforms hardware resources into a secure, usable operating environment.