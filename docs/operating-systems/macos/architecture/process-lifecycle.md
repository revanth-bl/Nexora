# macOS Process Lifecycle

## Overview

A **process** is a running instance of a program.

In macOS, process management is handled primarily by the **XNU kernel**, with user-space services such as **launchd** participating in process creation, supervision, and service management.

A simplified lifecycle is:

```text
Program
   │
   ▼
Process Created
   │
   ▼
Running
   │
   ├── Waiting
   ├── Sleeping
   ├── Stopped
   └── Running
   │
   ▼
Terminated
```

Understanding the process lifecycle is essential for system administration, performance troubleshooting, debugging, and understanding how macOS executes applications.

---

# What is a Process?

A process is a running program together with the resources required for its execution.

A process can have:

- Virtual address space
- Threads
- File descriptors
- Credentials
- Environment variables
- Signal handlers
- Process identifiers
- Scheduling information

Simplified:

```text
Process
│
├── Address Space
├── Threads
├── File Descriptors
├── Credentials
├── Environment
└── Kernel Resources
```

---

# Process vs Program

A **program** is a file containing executable instructions.

A **process** is the running instance of that program.

```text
Program
   │
   │ Execute
   ▼
Process
```

For example:

```text
/usr/bin/python3
```

is a program.

When it is executed:

```bash
python3 script.py
```

the operating system creates a process.

---

# Process Identifier

Every process has a unique **PID (Process ID)**.

Display processes:

```bash
ps
```

Display all processes:

```bash
ps aux
```

Example:

```text
PID   COMMAND
1     launchd
```

The PID allows the operating system and administrators to identify a specific process.

---

# PID 1

The primary system `launchd` process runs as:

```text
PID 1
```

The simplified process hierarchy begins with:

```text
launchd
   │
   ├── System Services
   ├── Daemons
   ├── User Services
   └── Applications
```

`launchd` is responsible for starting and managing many system services.

---

# Parent and Child Processes

Processes can create other processes.

The process that creates another process is commonly called the **parent**.

The newly created process is the **child**.

```text
Parent Process
      │
      ├── Child Process A
      │
      └── Child Process B
```

Each process normally has:

- PID
- Parent PID (PPID)

Display these relationships with:

```bash
ps -o pid,ppid,command
```

---

# Process Creation

Unix-derived operating systems traditionally use mechanisms based around:

```text
fork()
exec()
```

The conceptual process is:

```text
Existing Process
      │
      ▼
     fork()
      │
      ▼
Child Process
      │
      ▼
     exec()
      │
      ▼
New Program
```

macOS provides additional process-creation mechanisms as well, and applications do not necessarily need to manually use this exact sequence.

---

# fork()

`fork()` creates a new process based on an existing process.

Conceptually:

```text
Parent
  │
  ▼
fork()
  │
  ├──────────► Parent
  │
  └──────────► Child
```

The parent and child initially share many resources through operating-system mechanisms such as copy-on-write memory.

---

# exec()

The `exec` family of functions replaces the current process's program image with another executable.

Conceptually:

```text
Process
   │
   ▼
exec()
   │
   ▼
New Program
```

The process itself remains associated with its PID while its executable image is replaced.

---

# Copy-on-Write During Process Creation

When processes are created, macOS can use **copy-on-write** techniques.

Initially:

```text
Parent
   │
   └──────┐
          ▼
      Shared Pages
          ▲
   ┌──────┘
   │
 Child
```

If one process modifies a page:

```text
Parent ──► Original Page

Child ───► Private Copy
```

This avoids unnecessary immediate memory duplication.

---

# Process States

A process can exist in different execution states.

Conceptually:

```text
              ┌───────────┐
              │  Running  │
              └─────┬─────┘
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
       Sleeping   Waiting   Stopped
          │         │         │
          └─────────┴─────────┘
                    │
                    ▼
                Running
                    │
                    ▼
                Terminated
```

The exact state representation reported by tools such as `ps` is platform-specific.

---

# Running

A running process is actively executing or is eligible to execute on a CPU.

Multiple processes compete for CPU resources.

```text
CPU
 │
 ├── Process A
 ├── Process B
 └── Process C
```

The scheduler determines which runnable thread receives CPU time.

---

# Sleeping

A process or thread may sleep while waiting for an event.

Examples include waiting for:

- Input
- Network data
- A timer
- Filesystem activity
- Another process

Sleeping allows the CPU to execute other work.

---

# Waiting

Processes can wait for resources or events.

For example:

```text
Process
   │
   ▼
Waiting for I/O
   │
   ▼
I/O Completes
   │
   ▼
Runnable
```

Waiting is normal and does not automatically indicate a problem.

---

# Stopped Processes

A process can be stopped temporarily.

Signals can cause this behavior.

For example:

```bash
kill -STOP <PID>
```

The process can later be continued:

```bash
kill -CONT <PID>
```

Use these commands carefully, especially with system processes.

---

# Process Scheduling

The XNU kernel scheduler determines which runnable threads receive CPU time.

Simplified:

```text
Runnable Threads
       │
       ▼
Scheduler
       │
       ▼
CPU
```

Scheduling decisions consider factors such as:

- Priority
- Scheduling policy
- CPU availability
- Thread state
- System workload

---

# Threads

A process can contain multiple threads.

```text
Process
   │
   ├── Thread 1
   ├── Thread 2
   ├── Thread 3
   └── Thread 4
```

Threads within a process share the process's address space and many other resources.

---

# Multithreading

Applications commonly use multiple threads for:

- User interfaces
- Networking
- File operations
- Background processing
- Parallel computation

Example:

```text
Application
    │
    ├── UI Thread
    ├── Network Thread
    ├── Worker Thread
    └── Background Thread
```

A multi-threaded application can perform different tasks concurrently.

---

# Signals

Signals provide a mechanism for notifying processes about events.

Common signals include:

| Signal | Meaning |
|---|---|
| `SIGTERM` | Request termination |
| `SIGKILL` | Force termination |
| `SIGSTOP` | Stop process |
| `SIGCONT` | Continue stopped process |
| `SIGHUP` | Hangup / commonly used to request reload |
| `SIGINT` | Interrupt |
| `SIGCHLD` | Child process state change |

Send a signal with:

```bash
kill -TERM <PID>
```

---

# SIGTERM

`SIGTERM` requests that a process terminate.

Example:

```bash
kill -TERM 1234
```

It is generally preferable to use `SIGTERM` before resorting to `SIGKILL`, because applications can handle `SIGTERM` and perform cleanup.

---

# SIGKILL

`SIGKILL` immediately terminates a process and cannot be caught or ignored by the process.

```bash
kill -KILL <PID>
```

or:

```bash
kill -9 <PID>
```

Because the process cannot perform normal cleanup, `SIGKILL` should normally be a last resort.

---

# Process Exit

A process eventually terminates.

This can happen because:

- The program completes normally
- The program calls an exit function
- The process receives a terminating signal
- The process crashes
- The operating system terminates it

Simplified:

```text
Running
   │
   ▼
Exit
   │
   ▼
Terminated
```

---

# Exit Status

Processes normally return an exit status.

Conventionally:

```text
0
```

indicates success.

Non-zero values generally indicate some form of failure.

For example:

```bash
some-command
echo $?
```

The second command displays the exit status of the previous command.

---

# Parent Waiting for Child

A parent process can wait for a child process to terminate.

Conceptually:

```text
Parent
   │
   ├── Creates Child
   │
   ├── Waits
   │
   ▼
Child Terminates
   │
   ▼
Parent Receives Status
```

Unix systems commonly use mechanisms such as:

```c
wait()
waitpid()
```

for this purpose.

---

# Zombie Processes

A **zombie process** is a child process that has terminated but whose parent has not yet collected its exit status.

Conceptually:

```text
Child
   │
   ▼
Terminates
   │
   ▼
Zombie
   │
   ▼
Parent Calls wait()
   │
   ▼
Removed
```

A zombie does not continue executing normally.

It primarily represents retained process-table information.

---

# Orphan Processes

An **orphan process** is a process whose original parent terminates before the child.

The operating system reassigns orphaned processes to an appropriate system process.

Conceptually:

```text
Parent
  │
  ▼
Child
  │
Parent exits
  │
  ▼
Child Reparented
```

This prevents the child from being left without a process hierarchy relationship.

---

# launchd and Process Management

`launchd` plays an important role in managing many macOS processes.

For services:

```text
launchd
    │
    ▼
Service Configuration
    │
    ▼
Process Started
    │
    ▼
Process Runs
    │
    ├── Exits
    └── Crashes
          │
          ▼
    launchd May Restart
```

Whether a service is restarted depends on its launchd configuration.

---

# Application Launch

A simplified graphical application launch looks like:

```text
User
 │
 ▼
Launch Application
 │
 ▼
Launch Services / System Frameworks
 │
 ▼
Application Process
 │
 ▼
Application Threads
```

The exact internal launch path varies depending on the application and macOS version.

---

# Process Hierarchy

The process hierarchy can be inspected using:

```bash
ps -axo pid,ppid,command
```

A simplified hierarchy might look like:

```text
launchd
 │
 ├── system daemon
 │
 ├── service
 │
 └── user process
       │
       ├── worker
       └── helper
```

---

# Viewing Processes

List processes:

```bash
ps aux
```

Display a specific process:

```bash
ps -p <PID>
```

Display process hierarchy information:

```bash
ps -axo pid,ppid,command
```

Find a process:

```bash
pgrep -fl <name>
```

---

# top

`top` provides a continuously updated view of running processes.

Run:

```bash
top
```

Sort by memory usage:

```bash
top -o mem
```

Sort by CPU usage:

```bash
top -o cpu
```

It can help identify:

- CPU-intensive processes
- Memory-intensive processes
- Process IDs
- Process states
- System load

---

# Activity Monitor

macOS provides **Activity Monitor** as a graphical process-management tool.

It can display:

- CPU usage
- Memory usage
- Energy usage
- Disk activity
- Network activity
- Process information

It is useful when diagnosing resource-heavy applications.

---

# Process Priority

Processes and threads can have different scheduling priorities.

macOS provides tools such as:

```bash
nice
```

and:

```bash
renice
```

For example:

```bash
nice -n 10 command
```

Priority adjustments should be used carefully because they affect CPU scheduling behavior.

---

# Process Resources

A process can consume multiple resources:

```text
Process
 │
 ├── CPU
 ├── Memory
 ├── File Descriptors
 ├── Network Connections
 └── Other Kernel Resources
```

Useful tools include:

```bash
top
```

```bash
ps aux
```

and:

```bash
lsof -p <PID>
```

---

# File Descriptors

Processes use file descriptors to access resources such as:

- Files
- Pipes
- Sockets
- Devices

Example:

```text
Process
 │
 ├── stdin  → 0
 ├── stdout → 1
 └── stderr → 2
```

Inspect open files and resources:

```bash
lsof -p <PID>
```

---

# Process Environment

Processes receive an environment containing variables.

Examples include:

```text
PATH
HOME
USER
SHELL
```

Inspect your environment:

```bash
env
```

A process's environment can influence its behavior and configuration.

---

# Process Termination Workflow

A practical termination sequence is:

```text
Identify PID
    │
    ▼
Send SIGTERM
    │
    ▼
Wait for graceful exit
    │
    ├── Exits → Done
    │
    └── Still running
            │
            ▼
       Investigate
            │
            ▼
       SIGKILL if necessary
```

Example:

```bash
kill -TERM <PID>
```

Then, only if necessary:

```bash
kill -KILL <PID>
```

---

# Troubleshooting Process Problems

When a process behaves abnormally:

```text
Identify Process
      │
      ▼
Check CPU Usage
      │
      ▼
Check Memory Usage
      │
      ▼
Check Open Files / Connections
      │
      ▼
Inspect Logs
      │
      ▼
Check Parent / launchd
      │
      ▼
Take Corrective Action
```

Useful commands:

```bash
ps -p <PID> -o pid,ppid,state,%cpu,%mem,command
```

```bash
lsof -p <PID>
```

```bash
top -o cpu
```

```bash
top -o mem
```

---

# Common Process Problems

Common issues include:

- High CPU usage
- Excessive memory usage
- Memory leaks
- Hung processes
- Repeated crashes
- Zombie processes
- Unexpected process restarts
- File descriptor exhaustion
- Network connection problems

---

# Important Commands

| Command | Purpose |
|---|---|
| `ps` | Display processes |
| `pgrep` | Find processes |
| `top` | Monitor processes |
| `kill` | Send signals |
| `killall` | Send signals to processes by name |
| `nice` | Start a process with adjusted priority |
| `renice` | Modify process priority |
| `lsof` | Display open files/resources |
| `launchctl` | Manage launchd services |
| `vmmap` | Inspect a process's virtual memory |
| `dtruss` | Trace system calls and signals where permitted |

---

# Key Concepts

| Concept | Description |
|---|---|
| Process | Running instance of a program |
| PID | Process identifier |
| PPID | Parent process identifier |
| Thread | Execution unit within a process |
| Parent | Process that creates or manages a child |
| Child | Process created by another process |
| Signal | Notification delivered to a process |
| Exit Status | Result returned when a process terminates |
| Zombie | Terminated child awaiting status collection |
| Orphan | Child whose original parent has exited |
| Scheduler | Kernel component that manages CPU execution |
| launchd | macOS service and process-management framework |

---

# Process Lifecycle Summary

The complete lifecycle can be summarized as:

```text
Program
   │
   ▼
Process Creation
   │
   ▼
Process Initialized
   │
   ▼
Threads Created
   │
   ▼
Runnable
   │
   ▼
Running
   │
   ├──────────────┐
   │              │
   ▼              ▼
Waiting        Sleeping
   │              │
   └──────┬───────┘
          │
          ▼
       Runnable
          │
          ▼
       Running
          │
          ▼
      Termination
          │
          ▼
    Exit Status Collected
          │
          ▼
    Process Resources Freed
```

---

# Summary

macOS process management is built on the process and threading facilities provided by XNU, with `launchd` managing many system and background services.

The key lifecycle is:

```text
Create
  │
  ▼
Initialize
  │
  ▼
Run
  │
  ├── Wait
  ├── Sleep
  └── Stop
  │
  ▼
Terminate
  │
  ▼
Cleanup
```

Understanding this lifecycle makes it easier to diagnose CPU and memory problems, understand parent-child relationships, manage services, interpret process states, and safely terminate problematic applications.