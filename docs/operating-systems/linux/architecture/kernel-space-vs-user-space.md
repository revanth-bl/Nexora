# Kernel Space vs User Space

## Overview

Modern operating systems divide memory into two separate areas:

- **Kernel Space** – Reserved for the operating system kernel.
- **User Space** – Used by user applications and processes.

This separation improves **security**, **stability**, and **system reliability** by preventing applications from directly accessing critical system resources.

---

## Architecture Overview

```text
+--------------------------------------------------+
|                 User Space                       |
|--------------------------------------------------|
| Web Browser                                      |
| Text Editor                                      |
| Terminal                                         |
| Media Player                                     |
| User Applications                                |
+--------------------------------------------------+
              │
              │ System Calls
              ▼
+--------------------------------------------------+
|                Kernel Space                      |
|--------------------------------------------------|
| Process Management                               |
| Memory Management                                |
| File Systems                                     |
| Device Drivers                                   |
| Networking                                       |
| Security                                         |
+--------------------------------------------------+
              │
              ▼
+--------------------------------------------------+
|                  Hardware                        |
|--------------------------------------------------|
| CPU | RAM | Disk | Keyboard | Network Card | GPU |
+--------------------------------------------------+
```

---

# What is Kernel Space?

**Kernel Space** is a protected memory area where the Linux kernel executes.

Only the kernel has unrestricted access to:

- CPU
- RAM
- Storage devices
- Hardware drivers
- Networking
- System resources

Normal applications cannot directly access kernel space.

---

## Responsibilities of Kernel Space

The kernel is responsible for:

- Process scheduling
- Memory management
- File system management
- Device driver management
- Hardware communication
- Network stack
- Security and permissions
- Interrupt handling

---

## Characteristics

- Runs in **privileged mode (Ring 0)**.
- Has complete access to hardware.
- Shared by all running processes.
- A kernel crash can bring down the entire operating system.

---

## What is User Space?

**User Space** is where normal applications execute.

Examples include:

- Terminal
- Firefox
- Chrome
- VS Code
- Python programs
- Games
- Database servers

Applications in user space have limited privileges and cannot directly access hardware.

---

## Responsibilities of User Space

Applications perform tasks such as:

- Reading user input
- Displaying graphics
- Processing data
- Running scripts
- Communicating with the kernel through system calls

---

## Characteristics

- Runs with restricted permissions.
- Cannot directly access hardware.
- Cannot access another process's memory.
- Crashes usually affect only the application itself.

---

# Why Separate Kernel Space and User Space?

Without this separation, any application could:

- Delete system memory
- Modify kernel data
- Corrupt hardware
- Crash the operating system
- Bypass security

Separating the two improves:

- Security
- Stability
- Reliability
- Process isolation

---

# Communication Using System Calls

Applications cannot directly communicate with hardware.

Instead, they request services from the kernel using **system calls**.

Example:

```text
Application
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

When a program opens a file:

```c
open("notes.txt", O_RDONLY);
```

The `open()` function triggers a system call, allowing the kernel to safely access the filesystem.

---

# Memory Protection

Each user process receives its own virtual address space.

Example:

```text
Process A
+-------------+
| Private RAM |
+-------------+

Process B
+-------------+
| Private RAM |
+-------------+
```

Process A cannot directly access Process B's memory.

Only the kernel manages memory allocation and protection.

---

# Privilege Levels

Modern CPUs support multiple privilege levels.

Linux primarily uses:

| Level | Description |
|--------|-------------|
| Ring 0 | Kernel Space |
| Ring 3 | User Space |

Kernel code executes with the highest privilege, while applications run with limited permissions.

---

# Context Switching

When a program requests a kernel service:

1. CPU switches from User Mode to Kernel Mode.
2. Kernel performs the requested operation.
3. Control returns to User Mode.

Example:

```text
User Program
      │
      ▼
System Call
      │
      ▼
Kernel Mode
      │
      ▼
Hardware Access
      │
      ▼
Return to User Mode
```

This transition is called a **context switch** (or more precisely, a mode switch between user mode and kernel mode).

---

# Examples

### Reading a File

```text
Application
      │
open()
      │
Kernel
      │
Disk
```

---

### Sending Data Over Network

```text
Browser
      │
send()
      │
Kernel Network Stack
      │
Network Card
```

---

### Writing to Screen

```text
Application
      │
write()
      │
Kernel
      │
Display Driver
      │
Monitor
```

---

# Advantages of Separation

- Prevents unauthorized hardware access.
- Protects the operating system from faulty applications.
- Isolates processes from each other.
- Improves system security.
- Increases overall stability.

---

# Common Commands

Show kernel version:

```bash
uname -r
```

Display kernel information:

```bash
uname -a
```

View loaded kernel modules:

```bash
lsmod
```

Load a kernel module:

```bash
sudo modprobe <module_name>
```

Display CPU architecture:

```bash
lscpu
```

Display kernel messages:

```bash
dmesg
```

---

# Best Practices

- Avoid running applications as the root user unless necessary.
- Install only trusted kernel modules.
- Keep the kernel updated with security patches.
- Minimize unnecessary system calls in performance-critical applications.
- Never modify kernel memory directly unless developing kernel code.

---

# Key Takeaways

- Linux separates execution into **Kernel Space** and **User Space**.
- Kernel Space has full access to hardware and manages system resources.
- User Space runs applications with limited privileges.
- Applications communicate with the kernel through **system calls**.
- This separation improves security, stability, and process isolation.

---

## Related Topics

- Linux Architecture
- Boot Sequence
- System Calls
- Memory Management
- Process Lifecycle
- Kernel