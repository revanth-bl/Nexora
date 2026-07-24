# Process Lifecycle

## Overview

Every program running on a Linux system is executed as a **process**. The **process lifecycle** describes the sequence of stages a process goes through—from its creation to its termination.

Understanding the process lifecycle is essential for system administration, performance tuning, debugging, and process management.

---

# Process Lifecycle Diagram

```text
             New
              │
              ▼
           Ready
              │
              ▼
           Running
          ↙       ↘
 Waiting/Blocked   Ready
          │
          ▼
       Running
          │
          ▼
      Terminated
```

---

# What is a Process?

A **process** is an instance of a running program.

For example:

```text
Program: firefox
Running Instance: Process
```

Each process has:

- Process ID (PID)
- Parent Process ID (PPID)
- Memory allocation
- Open files
- CPU state
- Priority
- Security credentials

---

# Process Creation

A process is created when a user or another process starts a program.

Linux creates new processes using system calls such as:

- `fork()`
- `exec()`
- `clone()`

Typical sequence:

```text
Parent Process
      │
    fork()
      │
      ▼
 Child Process
      │
    exec()
      │
      ▼
 Program Starts
```

Example:

```bash
firefox
```

The shell creates a new process to launch Firefox.

---

# Process States

A Linux process moves through several states during its lifetime.

---

## 1. New

The process is being created.

During this stage:

- Process Control Block (PCB) is initialized.
- PID is assigned.
- Required resources are allocated.

This state exists only briefly.

---

## 2. Ready

The process is prepared to run but is waiting for CPU time.

Characteristics:

- Loaded into memory
- Waiting in the scheduler queue
- Ready for execution

Example:

```text
Ready Queue

Process A
Process B
Process C
```

---

## 3. Running

The CPU is actively executing the process instructions.

Only a limited number of processes can run simultaneously, depending on the number of CPU cores.

While running, a process may:

- Complete execution
- Request I/O
- Be interrupted
- Be preempted by the scheduler

---

## 4. Waiting (Blocked)

A process enters the waiting state when it cannot continue until an event occurs.

Common reasons include:

- Waiting for disk access
- Waiting for keyboard input
- Waiting for network data
- Waiting for another process

Example:

```text
Running
    │
Read File
    │
    ▼
Waiting
```

Once the required event completes, the process returns to the **Ready** state.

---

## 5. Terminated

A process reaches the terminated state when it finishes execution or is stopped.

Termination may occur because:

- Program completed successfully
- User closed the application
- Process received a kill signal
- Fatal error occurred

Resources such as memory and file descriptors are released by the kernel.

---

# Process State Transitions

```text
          New
           │
           ▼
         Ready
           │
           ▼
        Running
       ↙   │   ↘
Waiting  Exit  Ready
   │
   ▼
 Ready
```

---

# Parent and Child Processes

Linux organizes processes in a hierarchical structure.

Every process (except the first one) has a **parent process**.

Example:

```text
systemd (PID 1)
      │
      ├── bash
      │      │
      │      ├── vim
      │      └── python
      │
      └── sshd
```

The parent process can create child processes using `fork()`.

---

# Process Scheduling

The Linux scheduler determines which process receives CPU time.

Scheduling is based on:

- Priority
- Nice value
- CPU availability
- Scheduling policy

This ensures fair CPU allocation among processes.

---

# Context Switching

When the CPU switches from one process to another, Linux performs a **context switch**.

During a context switch, the kernel:

1. Saves the current process state.
2. Selects another ready process.
3. Restores the new process state.
4. Continues execution.

```text
Process A
    │
Save State
    │
    ▼
Linux Scheduler
    │
Restore State
    │
    ▼
Process B
```

---

# Process Control Block (PCB)

The kernel stores process information in a **Process Control Block (PCB)**.

The PCB contains:

- PID
- Process state
- CPU registers
- Program counter
- Scheduling information
- Memory information
- Open files
- Security credentials

The PCB allows the kernel to manage and switch between processes efficiently.

---

# Zombie Processes

A **zombie process** is a process that has finished execution but still has an entry in the process table because its parent has not yet collected its exit status.

Characteristics:

- Uses almost no system resources
- Retains its PID
- Appears with a `Z` state

---

# Orphan Processes

An **orphan process** is a process whose parent has terminated before it.

Linux automatically reassigns orphan processes to **systemd (PID 1)** or another designated init process.

---

# Common Commands

List running processes:

```bash
ps
```

Detailed process information:

```bash
ps aux
```

Interactive process viewer:

```bash
top
```

or

```bash
htop
```

Display process tree:

```bash
pstree
```

Find a process by name:

```bash
pgrep firefox
```

Terminate a process:

```bash
kill <PID>
```

Forcefully terminate a process:

```bash
kill -9 <PID>
```

Display current shell PID:

```bash
echo $$
```

---

# Best Practices

- Terminate processes gracefully before using force.
- Monitor CPU and memory usage regularly.
- Investigate long-running or blocked processes.
- Avoid creating unnecessary background processes.
- Use `top` or `htop` for real-time process monitoring.

---

# Key Takeaways

- A process is an executing instance of a program.
- The Linux process lifecycle includes **New**, **Ready**, **Running**, **Waiting**, and **Terminated** states.
- Processes are created using `fork()` and typically execute a new program using `exec()`.
- The Linux scheduler manages CPU allocation and performs context switches between processes.
- Parent-child relationships, process states, and efficient scheduling are fundamental to Linux process management.

---

## Related Topics

- Linux Architecture
- Boot Sequence
- Memory Management
- Kernel Space vs User Space
- System Calls
- Processes