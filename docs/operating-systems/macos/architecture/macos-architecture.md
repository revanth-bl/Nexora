# launchd and Services

## Overview

**launchd** is the primary system initialization and service-management framework in macOS.

It is responsible for starting and managing many background processes, daemons, agents, and scheduled tasks.

The central process is:

```text
launchd
PID 1
```

After the XNU kernel initializes, `launchd` becomes the first major user-space process and coordinates the startup of the rest of the operating system.

---

# High-Level Architecture

A simplified macOS startup flow is:

```text
Bootloader
    │
    ▼
XNU Kernel
    │
    ▼
launchd (PID 1)
    │
    ├── System Daemons
    │
    ├── System Agents
    │
    ├── User Agents
    │
    └── Other Services
```

---

# What is launchd?

`launchd` is Apple's unified service-management system.

It replaced several older mechanisms and provides a centralized way to manage:

- System daemons
- User agents
- Background services
- Scheduled jobs
- On-demand services
- System initialization

The executable is commonly located at:

```text
/sbin/launchd
```

---

# launchd as PID 1

The main system `launchd` process runs as:

```text
PID 1
```

You can verify this with:

```bash
ps -p 1
```

Or:

```bash
ps aux | head
```

The process hierarchy begins approximately like:

```text
launchd
   │
   ├── system services
   ├── daemons
   ├── agents
   └── user-session processes
```

Because `launchd` is responsible for managing critical services, problems with it can affect the entire operating system.

---

# Daemons vs Agents

macOS commonly distinguishes between **daemons** and **agents**.

## Daemon

A daemon is generally a background service that does not require a graphical user session.

Examples can include services responsible for:

- Networking
- System management
- Hardware
- Security
- Logging

Daemons can run independently of a logged-in graphical user.

---

## Agent

An agent generally operates within a user session.

Agents can provide functionality related to:

- User applications
- Desktop integration
- Notifications
- User-specific background tasks
- Synchronization

---

# System Daemons

System daemons are generally associated with:

```text
/Library/LaunchDaemons
```

and:

```text
/System/Library/LaunchDaemons
```

These services operate at the system level.

---

# System Agents

System agents are generally associated with:

```text
/System/Library/LaunchAgents
```

They provide background functionality associated with the operating system and user environment.

---

# User Agents

User-specific agents are commonly stored under:

```text
~/Library/LaunchAgents
```

These services run in the context of a particular user session.

---

# Launchd Job Types

A simplified model is:

```text
launchd
   │
   ├── LaunchDaemons
   │      └── System-level services
   │
   ├── System LaunchAgents
   │      └── macOS background services
   │
   └── User LaunchAgents
          └── User-session services
```

The exact service organization can vary between macOS releases.

---

# Property List Files

`launchd` jobs are commonly described using **property list files**:

```text
.plist
```

A plist contains configuration describing how a job should be managed.

A simplified example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC
"-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">
<dict>

    <key>Label</key>
    <string>com.example.service</string>

    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/example</string>
    </array>

    <key>RunAtLoad</key>
    <true/>

</dict>
</plist>
```

A plist describes the job rather than directly running the program.

---

# Common launchd Keys

Some commonly encountered keys include:

| Key | Purpose |
|---|---|
| `Label` | Unique identifier for the job |
| `Program` | Program to execute |
| `ProgramArguments` | Command and arguments |
| `RunAtLoad` | Start when the job is loaded |
| `KeepAlive` | Control whether the job should remain running |
| `WorkingDirectory` | Working directory |
| `EnvironmentVariables` | Environment variables |
| `StandardOutPath` | Standard output destination |
| `StandardErrorPath` | Standard error destination |
| `StartInterval` | Run at a specified interval |
| `StartCalendarInterval` | Schedule execution |

Not every job needs every key.

---

# launchctl

The primary command-line interface for interacting with `launchd` is:

```bash
launchctl
```

Display help:

```bash
launchctl help
```

---

# Listing Services

List services visible to the current user:

```bash
launchctl list
```

This can display information such as:

- PID
- Exit status
- Service label

For example:

```text
PID    Status    Label
-      0         com.example.service
1234   0         com.example.running
```

A `-` in the PID field generally indicates that the service is loaded but does not currently have a running process.

---

# Inspecting a Service

Use:

```bash
launchctl print system/com.example.service
```

For a user service, the domain may be different.

For example:

```bash
launchctl print gui/$(id -u)/com.example.service
```

The `print` command is useful for examining the current state and configuration of a service.

---

# Service Domains

Modern `launchctl` uses service domains to identify where jobs operate.

Examples include:

```text
system
```

for system services, and:

```text
user/<uid>
```

or:

```text
gui/<uid>
```

for user-related services.

For example:

```bash
launchctl print system
```

and:

```bash
launchctl print gui/$(id -u)
```

---

# Loading and Unloading Services

Older macOS documentation may refer to:

```bash
launchctl load
launchctl unload
```

These commands are associated with older service-management workflows.

Modern macOS generally uses:

```bash
launchctl bootstrap
```

and:

```bash
launchctl bootout
```

instead.

---

# Bootstrap

`bootstrap` loads a service into a launchd domain.

A conceptual example is:

```bash
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/com.example.service.plist
```

The exact domain and plist location must match the service being configured.

---

# Bootout

To remove a service from a launchd domain:

```bash
launchctl bootout gui/$(id -u)/com.example.service
```

Always verify the target before removing or stopping a service.

---

# Starting a Service

A service can be started with:

```bash
launchctl kickstart -k gui/$(id -u)/com.example.service
```

The exact domain depends on whether the service belongs to the system or a user session.

---

# Restarting a Service

`kickstart` can also be used to restart a service.

For example:

```bash
launchctl kickstart -k system/com.example.service
```

The `-k` option requests that an existing instance be terminated before restarting it.

---

# Service Status

Inspect a service with:

```bash
launchctl print system/com.example.service
```

For user services:

```bash
launchctl print gui/$(id -u)/com.example.service
```

This can reveal:

- Service state
- Process information
- Configuration
- Environment
- Resource information
- Exit status

---

# launchd and On-Demand Services

One of the important features of `launchd` is **on-demand service activation**.

A service does not necessarily need to run continuously.

Instead:

```text
Request
   │
   ▼
launchd
   │
   ▼
Start Service
   │
   ▼
Service Handles Request
   │
   ▼
Service May Exit
```

This can reduce unnecessary resource usage.

---

# KeepAlive

The `KeepAlive` property can tell `launchd` that a service should remain available according to specified conditions.

A simple configuration might contain:

```xml
<key>KeepAlive</key>
<true/>
```

More advanced configurations can use dictionaries to define conditions.

Careless use of `KeepAlive` can cause a failing process to restart repeatedly.

---

# RunAtLoad

The:

```xml
<key>RunAtLoad</key>
<true/>
```

property requests that the job be started when it is loaded.

This is useful for services that should begin immediately when their launchd job becomes active.

---

# Scheduled Jobs

`launchd` can schedule jobs.

One mechanism is:

```xml
<key>StartInterval</key>
<integer>3600</integer>
```

This represents an interval-based schedule.

Another mechanism is:

```xml
<key>StartCalendarInterval</key>
```

which can define calendar-based execution.

This makes `launchd` useful for many background automation tasks.

---

# Environment Variables

A launchd job can define environment variables.

Example:

```xml
<key>EnvironmentVariables</key>
<dict>
    <key>APP_ENV</key>
    <string>production</string>
</dict>
```

These variables are provided to the launched process.

---

# Program Arguments

A command and its arguments can be defined using:

```xml
<key>ProgramArguments</key>
<array>
    <string>/usr/local/bin/example</string>
    <string>--verbose</string>
</array>
```

This is preferable to relying on shell parsing when configuring launchd jobs.

---

# Standard Output and Error

A service can redirect output.

Example:

```xml
<key>StandardOutPath</key>
<string>/tmp/example.out</string>

<key>StandardErrorPath</key>
<string>/tmp/example.err</string>
```

For long-running production services, logging should be designed carefully rather than writing uncontrolled output to temporary files.

---

# launchd and Logging

Modern macOS uses the **Unified Logging System**.

The command-line interface is:

```bash
log
```

Examples:

```bash
log show
```

Stream logs:

```bash
log stream
```

Filter logs by process:

```bash
log stream --process launchd
```

For service troubleshooting, logs can provide information about:

- Startup failures
- Permission problems
- Crashes
- Service restarts
- Configuration errors

---

# launchd Service Lifecycle

A simplified lifecycle is:

```text
Plist Discovered
       │
       ▼
Job Loaded
       │
       ▼
launchd Registers Job
       │
       ▼
Trigger Occurs
       │
       ▼
Process Starts
       │
       ▼
Process Runs
       │
       ├── Success
       │
       ├── Exit
       │
       └── Crash
              │
              ▼
        launchd Evaluates Policy
```

Depending on its configuration, `launchd` may restart the process or leave it stopped.

---

# Troubleshooting Services

When a service does not work, follow a structured process.

## Step 1: Identify the Service

Find the service's label and plist.

```bash
launchctl list
```

---

## Step 2: Inspect the Service

```bash
launchctl print system/com.example.service
```

or:

```bash
launchctl print gui/$(id -u)/com.example.service
```

---

## Step 3: Check Logs

Use:

```bash
log show --last 1h
```

You can also stream logs:

```bash
log stream
```

---

## Step 4: Check the Executable

Verify that the program exists:

```bash
ls -l /path/to/program
```

Check permissions:

```bash
ls -l /path/to/program
```

---

## Step 5: Check the Plist

Inspect the plist:

```bash
plutil -p /path/to/service.plist
```

Check whether the plist is syntactically valid:

```bash
plutil -lint /path/to/service.plist
```

---

## Step 6: Check the Process

Use:

```bash
ps aux | grep example
```

or:

```bash
pgrep -fl example
```

---

# Common Service Problems

Common causes include:

- Invalid plist syntax
- Incorrect executable path
- Missing permissions
- Incorrect service domain
- Missing dependencies
- Failed executable
- Security restrictions
- Repeated crashes
- Incorrect environment variables
- Conflicting service configuration

---

# Security Considerations

Services execute with the privileges of their configured context.

A system-level daemon may have significantly more privileges than a normal user process.

Therefore:

```text
System Daemon
     │
     ▼
Higher Privileges
     │
     ▼
Greater Security Risk
```

When creating services:

- Use the minimum required privileges.
- Avoid unnecessary root execution.
- Validate executable paths.
- Protect plist files.
- Protect scripts and binaries.
- Avoid writable paths for privileged executables.
- Review environment variables carefully.

---

# launchd vs service

`launchd` is the service-management framework.

The actual service is the program being managed.

```text
launchd
   │
   ├── Service A
   ├── Service B
   └── Service C
```

So:

```text
launchd ≠ service
```

`launchd` manages the lifecycle of services.

---

# launchd vs cron

Both can execute scheduled tasks, but they are not identical.

| Feature | launchd | cron |
|---|---|---|
| macOS integration | Excellent | Legacy/Unix-oriented |
| Service management | Yes | No |
| On-demand activation | Yes | No |
| Process supervision | Yes | Limited |
| Calendar scheduling | Yes | Yes |
| User agents | Yes | Not designed around this |
| Modern macOS approach | Preferred | Legacy option |

For native macOS service and job management, `launchd` is generally the preferred mechanism.

---

# Important Commands

| Command | Purpose |
|---|---|
| `launchctl list` | List launchd jobs |
| `launchctl print` | Inspect service/domain state |
| `launchctl bootstrap` | Load a job into a domain |
| `launchctl bootout` | Remove a job from a domain |
| `launchctl kickstart` | Start/restart a service |
| `plutil -p` | Inspect plist contents |
| `plutil -lint` | Validate plist syntax |
| `log show` | Query unified logs |
| `log stream` | Stream unified logs |
| `ps` | Inspect processes |
| `pgrep` | Find processes |

---

# Key Concepts

```text
launchd
   │
   ├── PID 1
   │
   ├── System Daemons
   │
   ├── System Agents
   │
   ├── User Agents
   │
   ├── Scheduled Jobs
   │
   └── On-Demand Services
```

The important ideas are:

- `launchd` is the central macOS service manager.
- The system `launchd` process is PID 1.
- Services are described using property list files.
- Daemons generally provide system-level services.
- Agents generally operate within user sessions.
- `launchctl` is the main command-line management tool.
- Modern macOS uses service domains.
- `launchd` supports on-demand activation and process supervision.
- Unified Logging is useful for diagnosing service problems.

---

# Summary

`launchd` is one of the most important components of macOS system administration.

It connects the operating system's initialization process with the services that keep macOS functioning:

```text
XNU Kernel
     │
     ▼
launchd
     │
     ├── Daemons
     ├── Agents
     ├── Scheduled Jobs
     └── On-Demand Services
              │
              ▼
        Running System
```

Understanding `launchd`, `launchctl`, service domains, property lists, and service lifecycles provides a strong foundation for macOS administration, automation, troubleshooting, and security.