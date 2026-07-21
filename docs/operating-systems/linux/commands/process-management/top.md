# top

> Monitor running processes and system resource usage in real time.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Process Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`top` is an interactive command-line utility that provides a live view of running processes and system resource usage. It continuously updates information such as CPU usage, memory consumption, load average, uptime, and process activity.

Unlike `ps`, which displays a one-time snapshot, `top` refreshes automatically, making it ideal for monitoring a system in real time.

- **What does it do?** Displays real-time system and process information.
- **Why does it exist?** To help users monitor system performance and identify resource-intensive processes.
- **When is it commonly used?** Troubleshooting slow systems, finding high CPU or memory usage, and monitoring servers.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Monitor system resources in real time
- Identify high CPU and memory usage
- Sort processes by different metrics
- Kill processes directly from `top`
- Understand the information displayed

---

# ⚙️ Syntax

```bash
top [options]
```

---

# 📝 Parameters

`top` does not require positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-u user` | Display processes owned by a specific user |
| `-p PID` | Monitor only specific process IDs |
| `-d seconds` | Set refresh interval |
| `-n number` | Exit after a specified number of updates |
| `-b` | Run in batch mode (useful for scripts) |
| `-H` | Display individual threads |

---

# 💻 Basic Examples

## Example 1

```bash
top
```

Start the interactive process monitor.

---

## Example 2

```bash
top -u revanth
```

Display only processes owned by user `revanth`.

---

## Example 3

```bash
top -p 1234
```

Monitor only process ID `1234`.

---

## Example 4

```bash
top -d 2
```

Refresh the display every 2 seconds.

---

## Example 5

```bash
top -b -n 1
```

Run once in batch mode, useful for logging or scripting.

---

# 📤 Example Output

```text
top - 10:15:32 up 3 days,  5:22,  2 users,  load average: 0.12, 0.15, 0.09
Tasks: 218 total,   1 running, 217 sleeping
%Cpu(s):  5.3 us,  1.2 sy, 93.5 id
MiB Mem :  7850 total,  3245 free,  2180 used,  2425 buff/cache

PID USER   PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
2481 root   20  0 451M 31M 11M S 12.5 0.4 0:15.12 nginx
3156 user   20  0 912M 82M 20M S  4.8 1.0 0:02.54 chrome
```

---

# 🌍 Real-world Use Cases

- Diagnosing slow servers
- Finding memory leaks
- Monitoring application performance
- Identifying runaway processes
- Checking system load during deployments

---

# 🧠 How It Works

`top` continuously reads process information from the Linux `/proc` filesystem.

It refreshes the display at regular intervals, updating:

- CPU usage
- Memory usage
- Running processes
- System load
- Uptime
- Individual process statistics

The display updates until you quit the program.

---

# ⚠️ Common Mistakes

❌ Assuming `%CPU` can exceed 100%.

On multicore systems, a multithreaded process may use more than one CPU core.

---

❌ Forgetting to quit.

Press:

```text
q
```

to exit.

---

❌ Confusing load average with CPU usage.

Load average represents runnable and waiting processes—not CPU utilization alone.

---

# ✅ Best Practices

- Use `top` when troubleshooting performance problems.
- Sort by CPU or memory usage to identify resource-heavy processes.
- Combine with `kill` after identifying problematic processes.
- Use batch mode (`-b`) for scripts and automation.

---

# 🔒 Security Considerations

Most users can view system processes, but only privileged users can terminate or renice processes owned by others.

Avoid killing critical system processes unless you understand their purpose.

---

# 🚀 Performance Notes

`top` has minimal overhead and is suitable for continuous monitoring, even on production servers.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `ps` | Snapshot of running processes |
| `kill` | Terminate processes |
| `killall` | Kill processes by name |
| `htop` | Enhanced interactive process viewer |
| `vmstat` | System performance statistics |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ps` | One-time snapshot |
| `top` | Live monitoring |
| `htop` | More interactive interface with colors and mouse support |

---

# 🧪 Practice Exercises

### Beginner

Open `top` and identify the process using the most CPU.

---

### Intermediate

Monitor only processes owned by your user account.

---

### Advanced

Run `top` in batch mode and save its output to a log file.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `top` command?

**A:** It provides a real-time view of running processes and system resource usage.

---

### Intermediate

**Q:** What is the difference between `ps` and `top`?

**A:** `ps` shows a snapshot of processes, while `top` continuously updates the process list in real time.

---

### Advanced

**Q:** What does load average represent in `top`?

**A:** It indicates the average number of runnable or waiting processes over the last 1, 5, and 15 minutes. It measures system workload, not just CPU utilization.

---

# 🛠 Troubleshooting

**Problem:** High CPU usage.

**Solution:**

Sort processes by CPU usage and identify the application consuming resources.

---

**Problem:** System becomes slow.

**Solution:**

Use `top` to inspect CPU, memory, and load average, then investigate the processes responsible.

---

# 📚 Official Documentation

- `man top`
- `man proc`

---

# 📖 Further Reading

- Nexora: `ps`
- Nexora: `kill`
- Nexora: `killall`
- Nexora: `htop`

---

# 📌 Quick Summary

- `top` monitors processes in real time.
- Displays CPU, memory, uptime, load average, and process statistics.
- Refreshes continuously until exited.
- Press **q** to quit.
- Ideal for performance monitoring and troubleshooting.

---

# 🤝 Contributors

| Name | Contribution |
|------|--------------|
| Revanth B L | Initial version |

---

# 📝 Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-09 | Initial version |