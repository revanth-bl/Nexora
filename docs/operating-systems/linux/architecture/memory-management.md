# Memory Management

## Overview

Memory management is one of the core responsibilities of the Linux kernel. It is responsible for allocating, tracking, protecting, and reclaiming memory used by processes and the operating system.

Linux uses **virtual memory**, allowing each process to have its own isolated address space while efficiently utilizing physical RAM and disk storage.

Efficient memory management improves system performance, stability, and security.

---

# Memory Management Architecture

```text
                 User Applications
        +-------------------------------+
        | Browser | Editor | Database   |
        +-------------------------------+
                     │
                     ▼
            Virtual Address Space
                     │
                     ▼
        +-------------------------------+
        |      Linux Memory Manager     |
        |-------------------------------|
        | Virtual Memory                |
        | Paging                        |
        | Swapping                      |
        | Memory Allocation             |
        | Page Cache                    |
        | Memory Protection             |
        +-------------------------------+
                     │
                     ▼
              Physical RAM
                     │
                     ▼
             Swap Partition/File
```

---

# What is Memory Management?

Memory management is the process of:

- Allocating memory to processes
- Tracking memory usage
- Protecting memory between processes
- Releasing unused memory
- Managing virtual memory
- Handling swapping and paging

Without memory management, applications could overwrite each other's data or crash the operating system.

---

# Physical Memory (RAM)

Physical memory refers to the actual RAM installed in the computer.

Characteristics:

- Fast access speed
- Volatile (data is lost after power off)
- Limited capacity

Example:

```text
8 GB RAM
```

Linux attempts to maximize RAM usage for better performance by using free memory as cache when possible.

---

# Virtual Memory

Virtual memory allows each process to believe it has its own large, continuous block of memory, regardless of the amount of physical RAM available.

Benefits include:

- Process isolation
- Larger address spaces
- Efficient memory utilization
- Increased system stability

---

## Virtual Address Space

Each running process has its own virtual memory layout.

```text
+----------------------------+
| Stack                      |
+----------------------------+
| Heap                       |
+----------------------------+
| Shared Libraries           |
+----------------------------+
| Program Code (Text)        |
+----------------------------+
| Data                       |
+----------------------------+
```

The kernel maps these virtual addresses to physical memory.

---

# Paging

Linux divides memory into fixed-size blocks called **pages** (typically 4 KB).

Instead of moving entire programs into RAM, Linux loads only the pages that are currently needed.

Benefits:

- Efficient memory usage
- Faster application startup
- Reduced RAM consumption

---

# Swap Space

Swap is disk space used as an extension of RAM when physical memory becomes full.

Swap can be:

- Swap partition
- Swap file

Example:

```text
RAM Full
     │
     ▼
Move inactive pages
     │
     ▼
Swap Space
```

Since disk storage is much slower than RAM, excessive swapping can significantly reduce system performance.

---

# Page Cache

Linux uses unused RAM to cache frequently accessed files.

Benefits:

- Faster file access
- Reduced disk I/O
- Improved overall performance

Cached memory is automatically freed when applications need additional RAM.

---

# Memory Allocation

When a process requests memory:

1. The kernel checks available memory.
2. Virtual memory is allocated.
3. Virtual addresses are mapped to physical pages.
4. The process begins using the allocated memory.

When the process exits, the memory is released back to the system.

---

# Memory Protection

Linux prevents processes from accessing memory that belongs to other processes.

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

Only the kernel has permission to access all memory regions.

---

# Out of Memory (OOM) Killer

If both RAM and swap become exhausted, Linux activates the **OOM (Out of Memory) Killer**.

The OOM Killer:

- Identifies processes consuming excessive memory.
- Terminates one or more processes.
- Frees memory to keep the system running.

This prevents a complete system crash.

---

# Memory Mapping

Linux allows files and devices to be mapped directly into a process's address space using **memory mapping**.

Advantages:

- Faster file access
- Efficient sharing of data between processes
- Reduced copying of data

---

# Memory Management Flow

```text
Application
      │
Requests Memory
      │
      ▼
Linux Kernel
      │
Allocates Virtual Memory
      │
      ▼
Maps to Physical RAM
      │
      ▼
Uses Swap if Necessary
```

---

# Common Commands

Display memory usage:

```bash
free -h
```

Display detailed memory statistics:

```bash
cat /proc/meminfo
```

Show virtual memory statistics:

```bash
vmstat
```

Monitor processes by memory usage:

```bash
top
```

or

```bash
htop
```

Display swap usage:

```bash
swapon --show
```

Display process memory usage:

```bash
ps aux --sort=-%mem
```

View memory information:

```bash
cat /proc/meminfo
```

---

# Best Practices

- Monitor memory usage regularly.
- Avoid unnecessary background processes.
- Configure appropriate swap space.
- Upgrade RAM if frequent swapping occurs.
- Investigate applications with unusually high memory consumption.
- Use monitoring tools such as `top`, `htop`, and `vmstat`.

---

# Key Takeaways

- Linux memory management allocates, protects, and reclaims memory for processes.
- Each process uses its own virtual address space.
- Paging allows efficient use of RAM by loading memory in small blocks.
- Swap extends available memory using disk storage when RAM is insufficient.
- The Linux kernel manages memory protection, caching, and allocation to ensure system stability and performance.

---

## Related Topics

- Linux Architecture
- Kernel Space vs User Space
- System Calls
- Process Lifecycle
- Boot Sequence
- Filesystem Architecture